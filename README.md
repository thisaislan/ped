<a href="https://github.com/thisaislan/ped">
  <img src="https://github.com/thisaislan/just-images/raw/main/images/ped/presentation_banner.png">
</a>

<!-- Beautiful mountain -->

<p align="center">
    <a href="https://unity3d.com/get-unity/download">
        <img src="https://img.shields.io/badge/unity-tools-blue" alt="Unity Download Link"></a>
    <a href="https://github.com/thisaislan/persistence-easy-to-delete/blob/main/LICENSE.md">
        <img src="https://img.shields.io/badge/License-MIT-brightgreen.svg" alt="License MIT"></a>
</p>

<h3 align="center" style="text-align:center;">
	Everything starts with: I want to save a boolean...
</h3><br>

Have you ever thought that I just want to save a boolean using Unity PlayerPrefs? Or just wanted an easy way to see data saved in Unity, just to see if everything is ok or to change something? Or maybe you're tired of dealing with old scripts for saving files, deleting files, and so on in every project you work on. If yes, I feel you, and you know why I created Ped!

<br>

## What's Ped?

In short `Persistence easy to delete`, or just `Ped`, is a small library to easily handle persistence in Unity editor and abstract persistence flow in Unity projects.

Why do we have to settle for saving just float, int and string with PlayerPrefs? We don't have to. With Ped we can use Unity's `PlayerPrefs` to persist`bool, byte, sbyte, char, decimal, double,float, int, uint, long, ulong, short, ushort, string` and also `object`. Yeah, an entire object!! :open_mouth:

Ok, maybe would be better save objects as files, so to our happiness Ped also abstracts the logic to persist object as `files`, you just need to ask.

Ped also compresses data to save space and protect it, and uses a similar approach with all keys used, so your data can be well saved!! :blush:

<br>
<h4 align="center" style="text-align:center;">

  Wanna use Ped already? Click <a href="https://github.com/thisaislan/persistence-easy-to-delete">here</a>

  <a href="https://github.com/thisaislan/persistence-easy-to-delete">
    <img src="https://github.com/thisaislan/just-images/raw/main/images/ped/mini_logo.png">
  </a>
</h4>
<br>

<hr>

## How can Ped help you and your project?

### Providing an easy way to handle persistence in the editor

After install Ped... Ok, maybe it is important talk a little about how to install Ped. You can do this from Git following these steps:

1. Copying git url https://github.com/thisaislan/persistence-easy-to-delete.git

2. Click on `Window/Package Manager` in Unity Editor

3. Click on add package button ![Add package button](images/add_package.png) 

4. Select `Add package from git URL...`

![Add package button](https://github.com/thisaislan/just-images/raw/main/images/ped/add_method_package_selection.png) 

5. Past the Ped url

![Add package button](https://github.com/thisaislan/just-images/raw/main/images/ped/past_ped_url.png) 

6. Press `Enter` or clink on the `Add` button

Now, with Ped properly installed, you can start using it without further preparation! :satisfied:

<br>

Okay you're probably wondering about data manipulation, fair enough, let's see a little bit about that.

Once the installation is complete, you will see two new folders inside of the Assets folder, `Ped` and `Settings` (in case these folders already exist, Ped will use the existing ones). Inside of the Settings folder you will see a file called `PedSettings` and inside of the Ped folder you can se a file called `PedData`:

![Add package button](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_files.png)

**PedSettings** is a control center for actions of Ped. Here you can choose the data you want to use and define behaviors.

**PedData** is where data will be stored when the game is running in the editor. Through this file you can change any data, add new inputs, remove existing ones or just change their values.

(Don't worry, if you accidentally delete these files, Ped always creates new ones when they're gone. :wink:)

<br>
<h1 align="center" style="text-align:center;"></h1>

### Giving a simple and easy code to deal with data

Ok, Ok. Maybe it's time to show the code.

Let's say you just want to save a humble boolean using PlayerPrefs (yes, the same boolean I wanted to save), with Ped you just need to do this:

```csharp
  Ped.SetPlayerPrefs(booleanKey, yourBooleanValueHere);
```

The same to string:

```csharp
  Ped.SetPlayerPrefs(stringKey, yourStringValueHere);
```

And with Long:

```csharp
  Ped.SetPlayerPrefs(longKey, yourLongValueHere);
```

ulong:

```csharp
  Ped.SetPlayerPrefs(uLongKey, yourULongValueHere);
```

Ok, you got the idea! :smirk:

<br>

But just for a moment, for some reason that I don't know, we decided to save an entire object using PlayerPrefs. Okay, maybe now things get a little complicated. Are you prepared?

You need to do this:

```csharp
  Ped.SetPlayerPrefs(objectKey, yourObjectHere);
```

So, as you can see, if you know how to save one thing using Ped, you can save anything. And if you (like me) prefer to save objects as files, just do the following:

```csharp
  Ped.SetFile(objectKey, yourObjectHere);
```

Ped will save your data as a PlayerPrefs or file (depending on the method used) inferring and using the object's type.

<br>

To retrieve any value from Ped just use Get methods with correct key and type, for example if I want to retrieve my precious boolean saved as PlayerPrefs previously, I need to use this:

```csharp
  Ped.GetPlayerPrefs(booleanKey, (bool booleanRetrieved) =>
      {
          // Do something with the retrieved value
      });
```

To retrieve the object saved as file:

```csharp
  Ped.GetFile(objectKey, (ObjectType objectRetrieved) =>
      {
          // Do something with the retrieved value
      });
  ```

<br>

Now you might be thinking "what if I don't know if the save exists?"

In this case you can use:

```csharp
  Ped.HasPlayerPrefsKey<TypeOfTheData>(key, (bool result) =>
    { 
      // Do something with the result
    });
```

or

```csharp
  Ped.HasFileKey<TypeOfTheData>(key, (bool result) => { 

      });
```

Or if you're feeling really naughty, you could just try this :smiling_imp::

```csharp
  Ped.GetFile(ObjectType, (ObjectType objectRetrieved) =>
      {
          // Do something with the retrieved value
      }, () => {
          // Do something if the value does not exist
      });
```

<br>

Ped has some few methods and approaches designed to help you with PlayerPrefs and files. Below you can see all the public methods you will find on Ped.

<table>
  <thead>
    <tr>
      <th align="left">  Feature  </th>
      <th align="left">  Description  </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">  Serialize  </td>
      <td align="left">  Compress and serialize a object  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  Deserialize  </td>
      <td align="left">  Decompress and deserialize a object  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  SetPlayerPrefs  </td>
      <td align="left">  Saves PlayerPrefs with a specific key, type and value  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  GetPlayerPrefs  </td>
      <td align="left">  Loads PlayerPrefs with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeletePlayerPrefs  </td>
      <td align="left">  Deletes PlayerPrefs with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeleteAllPlayerPrefs  </td>
      <td align="left">  Deletes all PlayerPrefs key and values by calling PlayerPrefs.DeleteAll()  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  HasPlayerPrefsKey  </td>
      <td align="left">  Returns true if the given key exists in PlayerPrefs, otherwise returns false  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  SavePlayerPrefs  </td>
      <td align="left">  Writes all modified preferences to disk by calling PlayerPrefs.Save()  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  SetFile  </td>
      <td align="left">  Saves file with a specific key, type and e value  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  GetFile  </td>
      <td align="left">  Loads file with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeleteFile  </td>
      <td align="left">  Deletes file with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeleteAllFiles  </td>
      <td align="left">  Deletes all files saved  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  HasFileKey  </td>
      <td align="left">  Checks if exists a file with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeleteAll  </td>
      <td align="left">  Deletes all data, both files and PlayerPrefs  </td>
    </tr>
  </tbody>
</table>

<br>

Some methods, such as Gets and Sets, have flags to help you perform specific actions. For example with the code below it is possible to do a destructive get, that is, PlayerPrefs will be destroyed after obtaining it. :flags:

```csharp
  Ped.GetPlayerPrefs(booleanKey, actionIfHasResult, Ped.PlayerPrefsGetMode.Destructive);
```

<br>
<h1 align="center" style="text-align:center;"></h1>

### Allowing you a convenient alternative to manipulating the data when using Unity

Every time you use a Set method of Ped in the Unity editor, the value will be saved in the PedData file being used. As in the image below:

![PedData in editor](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_data_editor.png)

<!-- 
  A red Plummer with red clothes and mustache...
  Maybe it has an oval shape!? 
  No, I think it's another one, maybe a doctor, I don't know
-->

Therefore, it is possible to change, add or remove any data whenever you need it, also in the middle of a run in the editor. You can change the value, key and even the type by the PedData, just be careful not to break your game... :sweat_smile:

<br>

But don't worry, if you edit a field and want to check if everything is ok, just go to `Tools/Ped/Validate PedData` (or just use `Shift+F11`) and Ped will perform a validation on your data and let you know in the `console` if something wrong happened (we'll see more about validation later :wink:).

<br>

You probably noticed the `Avoid Changes` option in the image, this flag allows us to use the data, see the changes when Unity is in play mode and reset the data to the same previous values when exit of play mode. Very useful when we don't want to lose a specific set of data but want to use it to test the game's behavior.

![PedData avoid changes flag](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_data_avoid__changes_flag.png)

<br>
<h1 align="center" style="text-align:center;"></h1>

### Giving more information about the data usage

Perhaps another thing you noticed in the last image was the `Info` field. If you expand this field, you can see more information about the PedData file.

![PedData info](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_data_info.png)

<!-- My dream share that file T.T -->

in possession of this information you can track how your game is using the data, if has a excessive numbers of Gets or Sets, or just now how many times you have used that file (maybe you're a little too attached to him :heartpulse:).

<br>
<h1 align="center" style="text-align:center;"></h1>

### Enabling the use and sharing of multiple sets of data

Let's say you're creating a game and in that game you can choose different characters, that characters can have different sets of items and different amounts of money. This means that every time you want to test a specific character with a specific set of items and a specific amount of money, you need to set all the data before starting a test, right? Good luck! :clock1230:

![PedData avoid changes flag](https://github.com/thisaislan/just-images/raw/main/images/ped/characters.png)

<!-- 
  I could have hidden something in that picture
  what a shame : /
  (Or maybe I have... who knows)
-->

Maybe Ped can help you with that task, just create as many PedData as you need, fill each PedData with proper data, go to the `PedSettings` file and define the PedData file you want to use, and done, you have all set of data you need to test your game (may that is a nice moment to use the Avoid Changes flag).

![Selecting PedData](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_settings_select_ped_data.png)

<!-- Interesting characters... -->

Another cool part of this approach is that you can share your PedFiles with your team, so you only have to do it once. :heart_eyes:

> **_Tip_**: If your project uses git, stay smart with how you and your team are going to handle git for sharing the files.

<br>
<h1 align="center" style="text-align:center;"></h1>

### Helping with changes data validation

Along with save booleans Ped was built thinking about an important aspect of development (at least for me), the democratization of development. If you're familiar with Unity, you probably you know how to find saved files, how to edit a json, and how to reset a PlayerPrefs. But if you're not familiar with these things, you might have trouble figuring out how to do these things and how to make sure the new data changes are correct.

So in this case, Ped works by creating an easy place to show your data saved in Unity (as shown before), but it also lets you run validation on your data whenever you want, just press `Shift+F11` or `Tools/Ped/Validate PedData`. :sunglasses:

![PedData validation menu](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_data_validation_menu.png)

(As you can see Ped has some options and shortcuts, feel free to explore them. :wink:)

Validation will be performed automatically every time Ped realizes that the data has changed or in the first run after opening Unity (you know, just in case). That option can be disabled in `PedSettings` just by uncheck the option `Verify Data On Run Start`

During validation, Ped will show all errors in the `console`, even if the error was in the `Custom Serializer`... Witch bring us to the next topic!

<br>
<h1 align="center" style="text-align:center;"></h1>

### Giving us the possibility to use custom serializers easily

I know you saw that section in the PedSettings:

![PedData custom serializer](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_settings_custom_setitngs.png)

And yes, as the name suggests, you can drop in the `Custom Serializer` field a class to be used as the serializer class by Ped. That class needs to be:

```text 
  - Public
  - Not Static
  - Cannot be inside a custom assembly
  - Implements IPedSerializer interface
  - Implements Serializer and Deserializer methods
  - And it should only be one class in the file (inner classes can be used)
```

![PedData custom serializer](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_settings_custom_setitngs_illustration.png)

<br>

And now Ped is read to use the new serializer class even after the build (don't worry, Ped knows how to do this).

What!? Ho! Yeah! You are probably thinking about the field `Custom Serializer Path`, well it is indeed just the path to the file. :grin:

> **_Tip_**: If your project uses git, don't forget to push the changes in the PedSettings file to your team.

<br>

<hr>

## Question I was asked about Ped

> ### After installing Ped, something appears in the assets folder. Is this normal?

Yep, Ped always tries to create a PedData and a PedSettings if it doesn't find these files in the project.

This happens due to the pillar of democratization of development, which is why Ped always tries to help solve any problem that may cause some frustration in its use. :relaxed:

<br>

> ### Will Ped grow into a big tool?

To be sincere, I have no plans to turn Ped into a huge tool, I think this tool can help with a specific task and it should be so. So at least for now I don't think about creating the new Odin or anything like that, lol.

<br>

> ### I'm starting with Unity now, is Ped for me?

Totally!! :joy:But I strongly recommend you look up a little bit about [PlayerPrefs](https://docs.unity3d.com/ScriptReference/PlayerPrefs.html), [save files](https://www.youtube.com/watch?v=XOjd_qU2Ido) and [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) in Unity, just to know a little bit about these topics.

<br>

> ### Why is the key in Ped a key and type pair?

Maybe I was a bit swayed by the PlayerPrefs idea, where you need to say what kind of data you want to get (GetString, GetInt, GetFloat) and pass the correct key. To me this makes perfect sense, if you save a rock in the bank you can't get a diamond back  :gem: (lol) so you need to know the key and type and Ped will take that into account.

That means if you pass the correct key and the incorrect type Ped won't find the data, also there will be no crash. Ped just will answer as no data was found with that key and type.

In fact, when you try to save any data with Ped at runtime, Ped will create a key by concatenating the key you passed and the type, creating a unique key. For example, the follow code:

```csharp
  Ped.SetPlayerPrefs("MyPreciousBool", true);
```

The key resulting will be a hash of the string `MyPreciousBool~System.Boolean`.

That also means you can use the same key with different types and use the same key to save PlayerPrefs and Files without problems, although I really don't recommend that approach.

One more piece of information, if you use a key and type that already exists, the old value will be overwritten. :pencil2:

<br>

> ### Will there be more updates?

Probably. I believe...actually I now that there are some improvements that I can do yet, and probably some fixes in the future. So I think there will be some updates in the future

<br>

> ### Is there anything you don't like about Ped today?

There are few things actually. But nothing critical I think. :blush:

<br>

> ### Does Ped allow merge requests?

If you have something, just send to me! :stuck_out_tongue_winking_eye:

<br>

> ### I have a issue with Ped, can I open it on github?

Please! :yellow_heart:

<br>

> ### What you means with Ped always creates new PedData and PedSettings files when they're gone?

Every time you run the application or access `Tools/Ped`, Ped checks if these files exist, otherwise new files will be created.

<br>

> ### Why do you create another repository to talk about Ped instead of using the project's repository?

Because I wanted a silly presentation with a some images and I didn't want to put too many images in the projects of each person using Ped. So I kept the project lightly documented and created this new repository to show more about the project.

<br>

> ### I noticed that you removed some restrictions from the Set methods, why?

Because now it's possible to configure a custom serializer and I can't guarantee if the new serializer class has the same restrictions as the one used by the one used as default by Ped.

In addition, it is possible to see in the editor the result of the serialization in PedData, so it is easy to see any problems in the serialization. 

<br>

> ### Why isn't there a shortcut to duplicate files in the menu of the Ped?

Well, because you can use the standard shortcut to do this, `Ctrl+d` or `Command+D`. I don't think this feature will add much to the project (of course I could be wrong here, let me know now please :no_mouth:).

<br>

> ### Will all PedData and PedSettings files be compiled?

No way :exclamation: The only ScriptableObject that make it to the final build is `PedSerializeSettings`. This ScriptableObject is responsible for taking care of data from the custom serializer class, if it exists, and its use is internal to Ped.

<br>

No way :exclamation: The only ScriptableObject that make it to the final build is `PedSerializeSettings`. This ScriptableObject is responsible for taking care of data from the custom serializer class, if it exists, and its use is internal to Ped.

<br>

> ### Why is validation of flag settings true by default?

Because of pillar of democratization of development. Validation is a very important part of this process, whole team needs to feel free to change any data during development, and if for some reason someone accidentally mistypes something, Ped will help they next time that they try to run the project.

Of course, if the automatic validation for some reason takes too long, or is slowing down development, it is possible to disable this flag and relay the manual validation, just press `Shift+F11` or `Tools/Ped/Validate PedData` when the data has changed.

Remembering that the automatic validation will only be performed when the data is changed manually and in the first run, otherwise Ped understands that there is no need for validation.

<br>

> ### In the version 3.0.0 the method  to define a custom serializer class was removed, why?

It is very important to ask people for help to avoid errors, using this approach it was necessary to define the custom serializer class in two places, in the code and in the editor for validation purposes. Realizing that this could lead to human errors, I removed the method and created a way to configure the custom serializer just by the editor.

(again I could be wrong here, let me know now please :no_mouth:).

<br>

> ### Is the custom serializer path field just a path with no purpose?

Sincerely?! No :confused:! The `Custom Serializer` field is a `MonoScript`, and I don't know why but sometimes when you set that file, although you can see the file in the editor and you can push that change using git, when you try to get that info back using git, this field is reset by Unity. Because that Ped saves the path to the file and set the Custom Serializer field if needed.

<br>

> ### Does PedData have to be in gitignore?

I recommend it. Of course that depends on how you and your team works, but maybe that is the best alternative to avoid endless conflict...:scream: And if you put PedData, or even better the Ped folder, in gitignore, you can always share the PedData files just by uploading the file another way.

<br>

> ### Does Ped work for any project?

So far, Ped has been tested on small and medium-sized mobile projects. I'm not sure if Ped will work well in a big project, for example, but I think so. If you have a big project and you've already tried Ped, please let me know. :relaxed:

<br>

> ### Does Ped use reflection?

The short answer is yes. In editor mode, Ped uses reflection when validation is running. At runtime, Ped will use reflection once when the project is opened if the project has a custom serializer class, otherwise not.

<br>

> ### Why did Ped change its name??

Because at some point I was informed that the old name is a pejorative word in French. I'm sorry about the problem with this new name, but I can't stand the idea of creating a tool with an offensive name, even if it's unintentional.

<br>

> ### How do you pronounce the name Ped?

Easy, just pronounce the first "e" like the first "e" in "Education". :ab:

```text 
  Pediː
``` 
<br>

> ### What does the name Ped mean?

Persistence easy to delete, I chose this name because its acronym creates a good pun in my first language. :stuck_out_tongue_closed_eyes:

<!-- 
 
 My first language is Portuguese (Brazil). In Portuguese Ped is the present simple tense of the verb to ask. So when I say the following sentence in Portuguese:

 If you need save something ask to the Ped!

 Sounds like:

 If you need save something ask to the ask!

 lol

 I know, this is a silly joke, but now you know!
 (Keep it between us!!)
 ;)
 
-->

<!--
  ko-fi donation button 
 -->
<br>
<br>
<br>
<br>
<h4 align="center" style="text-align:center;">
  <a href="https://ko-fi.com/thisaislan">
    <img src="https://github.com/thisaislan/just-images/raw/main/images/ko-fi/ko-fi_donation_banner.gif" style="width: 460px">
  </a>
</h4>
<br>
<br>
<br>
<br>