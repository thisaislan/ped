<a href="https://github.com/thisaislan/ped">
  <img src="https://github.com/thisaislan/just-images/raw/main/images/ped/presentation_banner.png">
</a>

<!-- Beautiful mountain -->

<p align="center">
    <a href="https://unity3d.com/get-unity/download">
        <img src="https://img.shields.io/badge/unity-tools-blue" alt="Unity Download Link"></a>
    <a href="https://github.com/thisaislan/persistence-easy-to-delete/blob/main/LICENSE.md">
        <img src="https://img.shields.io/badge/License-MIT-brightgreen.svg" alt="License MIT"></a>
    <a href="https://chat.deepseek.com">
        <img src="https://img.shields.io/badge/%F0%9F%92%AC-DeepSeek%20AI-blue" alt="DeepSeek"></a>
</p>

<h3 align="center" style="text-align:center;">
	Everything starts with: I want to save a boolean...
</h3><br>

Have you ever thought, "I just want to save a boolean using Unity PlayerPrefs"? Or wanted an easy way to see the data saved in Unity, just to check if everything is ok or to change something? Or maybe you're tired of dealing with old scripts for saving files, deleting files, and so on in every project you work on. If yes, I feel you, and you know why I created Ped!

<br>

## What's Ped?

In short `Persistence easy to delete`, or just `Ped`, is a small library to easily handle persistence in the Unity editor and abstract the persistence flow in Unity projects.

Why do we have to settle for saving just float, int and string with PlayerPrefs? We don't have to. With Ped we can use Unity's `PlayerPrefs` to persist `bool, byte, sbyte, char, decimal, double, float, int, uint, long, ulong, short, ushort, string` and also `object`. Yeah, an entire object!! :open_mouth:

Ok, maybe it would be better to save objects as files, so to our happiness Ped also abstracts the logic to persist objects as `files`, you just need to ask.

Ped also compresses data to save space and protect it, and uses a similar approach for all the keys used, so your data can be well saved!! :blush:

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

After installing Ped... Ok, maybe it is important to talk a little about how to install Ped. You can do this from Git following these steps:

1. Copy the git URL https://github.com/thisaislan/persistence-easy-to-delete.git

2. Click on `Window/Package Manager` in the Unity Editor

3. Click on the add package button ![Add package button](images/add_package.png) 

4. Select `Add package from git URL...`

![Add package button](https://github.com/thisaislan/just-images/raw/main/images/ped/add_method_package_selection.png) 

5. Paste the Ped URL

![Add package button](https://github.com/thisaislan/just-images/raw/main/images/ped/past_ped_url.png) 

6. Press `Enter` or click on the `Add` button

Now, with Ped properly installed, you can start using it without further preparation! :satisfied:

<br>

Okay, you're probably wondering about data manipulation, fair enough, let's see a little bit about that.

Once the installation is complete, you will see a new folder inside the Assets folder, `Ped` (in case this folder already exists, Ped will use the existing one). Inside the Ped folder you can see a file called `PedData`:

**PedData** is where the data will be stored when the game is running in the editor. Through this file you can change any data, add new inputs, remove existing ones or just change their values. It is also in the PedData that you choose which data will be used by Ped, through the `In use` flag (enabling the flag on a PedData automatically disables it on the others).

(Don't worry, if you accidentally delete this file, Ped always creates a new one when it's gone. :wink:)

<br>
<h1 align="center" style="text-align:center;"></h1>

### Giving a simple and easy code to deal with data

Ok, Ok. Maybe it's time to show the code.

Let's say you just want to save a humble boolean using PlayerPrefs (yes, the same boolean I wanted to save), with Ped you just need to do this:
```csharp
  Ped.SetPlayerPrefs(booleanKey, yourBooleanValueHere);
```

The same for a string:

```csharp
  Ped.SetPlayerPrefs(stringKey, yourStringValueHere);
```

And with a long:

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

Ped will save your data as a PlayerPrefs or a file (depending on the method used), inferring and using the object's type.

<br>

To retrieve any value from Ped, just use the Get methods with the correct key and type, for example if I want to retrieve my precious boolean saved as PlayerPrefs previously, I need to use this:

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

Now you might be thinking, "what if I don't know if the save exists?"

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

Ped has a few methods and approaches designed to help you with PlayerPrefs and files. Below you can see all the public methods you will find on Ped.

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
      <td align="left">  Compress and serialize an object  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  Deserialize  </td>
      <td align="left">  Decompress and deserialize an object  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  SetSerializer  </td>
      <td align="left">  Sets a custom serializer class to be used by Ped instead of the built-in one  </td>
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
      <td align="left">  Saves a file with a specific key, type and value  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  GetFile  </td>
      <td align="left">  Loads a file with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeleteFile  </td>
      <td align="left">  Deletes a file with a specific key and type  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  DeleteAllFiles  </td>
      <td align="left">  Deletes all the files saved  </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="left">  HasFileKey  </td>
      <td align="left">  Checks if a file with a specific key and type exists  </td>
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

Some methods, such as Gets and Sets, have flags to help you perform specific actions. For example, with the code below it is possible to do a destructive get, that is, the PlayerPrefs will be destroyed after obtaining it. :flags:

```csharp
  Ped.GetPlayerPrefs(booleanKey, actionIfHasResult, Ped.PlayerPrefsGetMode.Destructive);
```

<br>
<h1 align="center" style="text-align:center;"></h1>

### Allowing you a convenient alternative to manipulate the data when using Unity

Every time you use a Set method of Ped in the Unity editor, the value will be saved in the PedData file being used. As in the image below:

![PedData in editor](https://github.com/thisaislan/just-images/raw/main/images/ped/ped_data_editor.png)

<!-- 
  A red Plummer with red clothes and mustache...
  Maybe it has an oval shape!? 
  No, I think it's another one, maybe a doctor, I don't know
-->

Therefore, it is possible to change, add or remove any data whenever you need it, even in the middle of a run in the editor. You can change the value, the key and even the type through the PedData, just be careful not to break your game... :sweat_smile:

<br>

But don't worry, if you edit a field and want to check if everything is ok, just open the PedData inspector and press the `Validate Data` button, Ped will validate your data (with a JSON syntax check included) and let you know if something went wrong (we'll see more about validation later :wink:).

<br>

<h1 align="center" style="text-align:center;"></h1>

### Showing the status of the data

At the top of the PedData inspector you'll find the `Status` card: with the `Use this PedData` button you can make your PedData the active one (this automatically disables the flag on the other PedData files), and with the `Block changes while the scene is running` button you can tell Ped to protect the file while the game is running (Ped creates a backup when the editor enters play mode and restores the previous values when it exits play mode). Very useful when we don't want to lose a specific set of data but want to use it to test the game's behavior.

<br>
<h1 align="center" style="text-align:center;"></h1>

### Enabling the use and sharing of multiple sets of data

Let's say you're creating a game and in that game you can choose different characters, and those characters can have different sets of items and different amounts of money. This means that every time you want to test a specific character with a specific set of items and a specific amount of money, you need to set all the data before starting a test, right? Good luck! :clock1230:

![PedData avoid changes flag](https://github.com/thisaislan/just-images/raw/main/images/ped/characters.png)

<!-- 
  I could have hidden something in that picture
  what a shame : /
  (Or maybe I have... who knows)
-->

Maybe Ped can help you with that task: just create as many PedData as you need, fill each PedData with proper data, mark the PedData you want to use with the `In use` flag, and done, you have all the sets of data you need to test your game (maybe that is a nice moment to use the Avoid Changes flag too). <br>

> **_Tip_**: Only one PedData can be in use at a time. If you mark more than one PedData as in use (for example, by duplicating a PedData that was already in use), Ped will resolve this automatically, keeping the oldest PedData active and unmarking the others when the data is accessed, warning you about it in the console. The inspector of a PedData that is in use but is not the active one shows a warning with a button to make it active.

<!-- image: screenshot of the PedData inspector with the Status card "Use this PedData" button and the duplicate warning -->

<!-- Interesting characters... -->

Another cool part of this approach is that you can share your PedFiles with your team, so you only have to do it once. :heart_eyes:

> **_Tip_**: If your project uses git, stay smart with how you and your team are going to handle git for sharing the files.

<br>
<h1 align="center" style="text-align:center;"></h1>

### Helping with changes data validation

Along with saving booleans, Ped was built thinking about an important aspect of development (at least for me), the democratization of development. If you're familiar with Unity, you probably know how to find saved files, how to edit a json, and how to reset a PlayerPrefs. But if you're not familiar with these things, you might have trouble figuring out how to do them and how to make sure the new data changes are correct.

So in this case, Ped works by creating an easy place to show your data saved in Unity (as shown before) and, with the `Validate Data` button on the PedData inspector, you can validate your data whenever you want. :sunglasses:

Validation checks the keys, types and values stored, including a JSON syntax check of the serialized values, and shows all errors directly on the inspector. :wink:

Validation is available whenever the scene is not running.

<br>
<h1 align="center" style="text-align:center;"></h1>

### Giving us the possibility to use custom serializers easily

Ped has a built-in serializer (based on Unity's `JsonUtility`) ready to use, but you can also define your own serializer class. That class needs to:

```text 
  - Be public and not static
  - Implement the IPedSerializer interface
  - Implement the Serialize and Deserialize methods
```

Then, to make Ped use it, just call the `SetSerializer` method once, before using Ped (like in a startup scene):

```csharp
  Ped.SetSerializer(new MyCustomSerializer());
```

Ped will use your serializer class for all serialization and deserialization, including in builds.

<br>

<hr>

## Questions I was asked about Ped

> ### After installing Ped, something appears in the assets folder. Is this normal?

Yep, Ped always tries to create a PedData if it doesn't find this file in the project.

This happens due to the pillar of democratization of development, which is why Ped always tries to help solve any problem that may cause some frustration in its use. :relaxed:

<br>

> ### Will Ped grow into a big tool?

To be sincere, I have no plans to turn Ped into a huge tool, I think this tool can help with a specific task and it should be so. So at least for now, I don't think about creating the new Odin or anything like that, lol.

<br>

> ### I'm starting with Unity now, is Ped for me?

Totally!! :joy: But I strongly recommend you look up a little bit about [PlayerPrefs](https://docs.unity3d.com/ScriptReference/PlayerPrefs.html), [save files](https://www.youtube.com/watch?v=XOjd_qU2Ido) and [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) in Unity, just to know a little bit about these topics.

<br>

> ### Why is the key in Ped a key and type pair?

Maybe I was a bit swayed by the PlayerPrefs idea, where you need to say what kind of data you want to get (GetString, GetInt, GetFloat) and pass the correct key. To me, this makes perfect sense: if you save a rock in the bank you can't get a diamond back :gem: (lol), so you need to know the key and the type, and Ped will take that into account.

That means if you pass the correct key and the wrong type, Ped won't find the data, and there will also be no crash. Ped will just answer as if no data was found with that key and type.

In fact, when you try to save any data with Ped at runtime, Ped will create a key by concatenating the key you passed and the type, creating a unique key. For example, the following code:

```csharp
  Ped.SetPlayerPrefs("MyPreciousBool", true);
```

The resulting key will be a hash of the string `MyPreciousBool~System.Boolean`.

That also means you can use the same key with different types and use the same key to save PlayerPrefs and files without problems, although I really don't recommend that approach.

One more piece of information: if you use a key and type that already exists, the old value will be overwritten. :pencil2:

<br>

> ### Will there be more updates?

Probably. I believe... actually I know there are some improvements that I can still do, and probably some fixes in the future. So I think there will be some updates in the future.

<br>

> ### Is there anything you don't like about Ped today?

There are a few things, actually. But nothing critical, I think. :blush:

<br>

> ### Does Ped allow merge requests?

If you have something, just send it to me! :stuck_out_tongue_winking_eye:

<br>

> ### I have an issue with Ped, can I open it on GitHub?

Please! :yellow_heart:

<br>

> ### What do you mean, Ped always creates new PedData files when they're gone?

Every time you run the application or access `Tools/Ped`, Ped checks if this file exists, otherwise a new one will be created.

<br>

> ### Why do you create another repository to talk about Ped instead of using the project's repository?

Because I wanted a silly presentation with some images and I didn't want to put too many images in the projects of each person using Ped. So I kept the project lightly documented and created this new repository to show more about the project.

<br>

> ### I noticed that you removed some restrictions from the Set methods, why?

Because now it's possible to configure a custom serializer, and I can't guarantee that the new serializer class has the same restrictions as the one used as default by Ped.

In addition, it is possible to see in the editor the result of the serialization in PedData, so it is easy to see any problem during the serialization. 

<br>

> ### Will the PedData files be compiled?

No way :exclamation: The PedData files are editor-only assets, used to see and edit data during development. Ped runs in your game using its code; the data (for the player) is stored in the PlayerPrefs and files at runtime, as it always was.

<br>

> ### Why is the `Validate Data` button not always available?

Validation is only available when the scene is not running, because changing or validating data while the game is running could break the current test state.

On the other hand, validation on demand is a good ally: the whole team needs to feel free to change any data during development, and if for some reason someone accidentally mistypes something, Ped will help them the next time they press the validate button.

> ### Why some features was added removed and added again?

Using the previous approach, it was necessary to define the custom serializer class in two places, in the code and in the editor, for validation purposes. Realizing that this could lead to human errors, I removed the method and created a way to configure the custom serializer just by the editor.

But then the editor configuration (a settings file to keep the serializer configuration) also proved to be extra overhead for a configuration that is pure code, so in version 5.0.0 the way to set a custom serializer class is again through the code, just with the `Ped.SetSerializer` method (validation, in turns, now uses the built-in serializer).

<br>

> ### Is the custom serializer configured only by code?

Yes. Since version 5.0.0 there is no settings file anymore: the custom serializer class is set only through the `Ped.SetSerializer` method, and the serializer used by the validation is the built-in one.

<br>

> ### Does PedData have to be in gitignore?

I recommend it. Of course, that depends on how you and your team work, but maybe that is the best alternative to avoid endless conflicts... :scream: And if you put PedData, or even better the Ped folder, in gitignore, you can always share the PedData files just by uploading the file another way.

<br>

> ### Does Ped work for any project?

So far, Ped has been tested on small and medium-sized mobile projects. I'm not sure if Ped will work well in a big project, for example, but I think so. If you have a big project and you've already tried Ped, please let me know. :relaxed:

<br>

> ### Does Ped use reflection?

The short answer is no. Since version 5.0.0, Ped uses its built-in serializer to validate the data in the editor and the serializer set by the code at runtime; no reflection involved.

<br>

> ### Why did Ped change its name?

Because at some point I was informed that the old name was a pejorative word in French. I'm sorry about the problem with this new name, but I can't stand the idea of creating a tool with an offensive name, even if it's unintentional.

<br>

> ### How do you pronounce the name Ped?

Easy, just pronounce the first "e" like the first "e" in "Education". :ab:

```text 
  Pediː
``` 
<br>

> ### What does the name Ped mean?

Persistence easy to delete. I chose this name because its acronym creates a good pun in my first language. :stuck_out_tongue_closed_eyes:

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