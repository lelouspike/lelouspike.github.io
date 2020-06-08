## Welcome to Lelou's Homepage
Twitter: @LelouSpike
Gmail: lelouspike@gmail.com

# 本页面包含的内容
Unity

# Unity学习

## Unity C# Survival Guide

### 改变GameObject的位置
A Vector3 is going to hold the x,y,and z position data of the player.
public Vector3 startPostion;
startPosition = new Vector3(0,0,0);
transform.postion = startPostion;

### User Input
All User Input needs to go inside the Update method.
Use an if statement and use the Input class. 
Input.GetKeyDown : allows to grab a key when we press it down
GetKeyDown means that you're holding the key down and GetKeyUp is checking for when you lift the key up.
Typing a Keycode.operator

// If the user hits the space key
if (Input.GetKeydown (Keycode.space))
{
We can say here Debug.Log ("space key");
}

### Simple Movement
the Translate tool on the Transform component
convert one meter per frame to one meter per second: * Time.deltaTime

Serialized the field to see it in the inspector
[Serialize Field]

axes: Edit>project settings>Input 
Horizontal and Vertical axis return to float values, mapped to left keys, right keys and A, D respectively

create float horizontalInput and assign it to that input manager
float horizontalInput = Input.GetAxis("Horizontal");

transform.Translate(newVector3(horizontalInput,0,0) * speed * Time.delatTime);

### Collectible GameObjects
To get started with collecting objects, we need to ensure that one thing is for sure.
Physics is enabled that we can actually run into this object.
IsTrigger must be checked that we can then pass through the object.
If IsTrigger is not checked, it's then a solid object.
We need to have collectible to have Physics. 

Unity has an internal method that automatically gets called when a collision occurs and that's called OnTriggerEnter, allow us to get information about the object that collided with us as well as perform any actions.

If you're working with a solid object, such as you didn't use IsTrigger, then you would use OnCollisionEnter.
Trigger is used for if the IsTrigger value on the collider is checked.

//This parameter here is going to store whatever object hit.
For example, if the player runs into it, the object player's going to be stored inside this collider variavle.

private void OnTriggerEnter(Collider, other)
//we are checking for the player.
{
 if(other.tag == "Player")
 {
 // simulate the experience of collecting an object
 Destroy(this.gameObject);
 }
}


### Pause System
//pause
if (Input.GetKeyDown(Keycode.Space))
{
 Time.timeScale = 0;
}

if(Input.GetKeyDown(Keycode.R))
{
 Time.timeScale = 1;
}
timeScale: 0是暂停，1是原速度，0.5是半速


## Rotations

### Quaternion Identity

private GameObject cubePrefab;

if (Input.GetKeyDown(keycode.Space))
{
 Instantiate(cubePrefab,Vector3.zero,Quaternion.identity);//没有rotation
 Instantiate(cubePrefab,Vector3.zero,Quaternion.Euler(x,y,z));//有rotation
}

### Quaternion Look Rotation
