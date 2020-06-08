## Welcome to Lelou's Homepage
Twitter: @LelouSpike
Gmail: lelouspike@gmail.com

# 本页面包含的内容
Unity

# Unity学习
## Unity C#教程学习
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

