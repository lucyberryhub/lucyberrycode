**🍓 Hey sweethearts! I’m Lucy Berry 💖**  
Welcome to my berry-licious coding world! 💻✨  

I’m all about:  
🍒 *Turning code into chic creations.*  
🍓 *Making apps that are as sweet as they are smart.*  
💋 *Adding a pinch of glam and a lot of berries to tech every day!*  

What you’ll find here:  
🍓 **Juicy Projects**: Code that’s ripe with creativity and style.  
🍒 **Berry Cute Designs**: Themes and apps inspired by sweetness and sass.  
🌟 **Passion for Innovation**: Mixing brilliance with a bit of berry magic.  

**✨ Bonus: I sprinkle berries into my code! ✨**  
Whether it’s Python 🍓, JavaScript 🍒, or C# 🫐, I’ll be creating a variety of projects with a berry twist inside.  

Let’s make the tech world berry fabulous together! 💄✨  
Follow me on my socials for more berry updates:  
🐦 **X (formerly Twitter)**: [@lucyberrycode](https://x.com/lucyberrycode)  
📸 **Instagram**: [lucyberrycode](https://instagram.com/lucyberrycode)  



# Lucy Berry's Sweet Coding Recipe Book

- [Cherry Berry File Handling & JSON Jar Magic - A Lovely, Girly Guide](#cherry-berry-file-handling--json-jar-magic---a-lovely-girly-guide)

---

### Cherry Berry File Handling & JSON Jar Magic - A Lovely, Girly Guide

[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)


---

### 🍒 **Cherry Berry File Handling & JSON Jar Magic - A Lovely, Girly Guide!** 🍒  

💖 Welcome, sugarplum! 🌸 Are you ready to sprinkle some magic into your coding journey? ✨ This tutorial is like baking a lovely berry pie – each step is sweeter than the last! Let’s dive into the sparkling world of **Cherry Berry File Handling** and turn your data into the cutest **JSON jars** ever. 🍒🎀  

---

#### 🌸 **Step 1: Setting Up Your Lucy Berry Folder**  

Every recipe starts with the perfect workspace. Let’s create a **Lucy Berry folder** to store all your precious data, like jars filled with love and sweetness! 🍓✨  

```csharp  
public static readonly string lucyBerryPath = Path.Combine(Path.GetTempPath(), "LucyBerry_Setting");  
```  

---

#### 🍓 **Step 2: Crafting the Sweetest File Names**  

Give your JSON jars a sweet label! Here’s how you name your files with love:  

```csharp  
string tableName = GetTableNameFromDbSet<T>();  
lucyBerryJsonFile = Path.Combine(lucyBerryPath, $"UpdateItem_{tableName}_{titleText}.json");  
```  

---  

#### 🍒 **Step 3: Preparing Your Basket for the Berries**  

Before adding the berries (data), make sure the basket (folder) is neat and ready! 🌸✨  

```csharp  
if (!Directory.Exists(lucyBerryPath))  
{  
    Directory.CreateDirectory(lucyBerryPath);  
}  
```  

---  

#### 🍓 **Step 4: Picking the Juiciest Berries (Fetching Data)**  

Pluck the sweetest, most colorful berries (data) from the database! 🍒🌸  

```csharp  
using (var dbContext = new AppDbContext())  
{  
    var dbSet = dbContext.GetDbSet<T>();  
    var data = await dbSet  
        .Where(item => EF.Property<string>(item, "Spec") == TitleText)  
        .ToListAsync();  
}  
```  

---  

#### 🍒 **Step 5: Packing the Berries into JSON Jars**  

Once you've picked your berries, store them neatly in your JSON jars! 🍓✨  

```csharp  
if (data != null)  
{  
    string jsonData = JsonConvert.SerializeObject(data, Formatting.Indented);  
    using (var stream = new FileStream(lucyBerryJsonFile, FileMode.Create, FileAccess.Write, FileShare.None))  
    using (var writer = new StreamWriter(stream))  
    {  
        await writer.WriteAsync(jsonData);  
    }  
}  
```  

---  

#### 🍓 **Step 6: Handling Little Oopsies with Love**  

If something goes wrong, don’t worry! A sprinkle of kindness can fix anything! 💖✨  

```csharp  
catch (Exception ex)  
{  
    MessageBox.Show($"エラーが発生しました: {ex.Message}", "エラー", MessageBoxButton.OK, MessageBoxImage.Error);  
}  
```  

---  

### **Conclusion: You're a Lucy Berry Star!** 🍓✨  

Congratulations, darling! 💖 You’ve just created the cutest **JSON jar system** ever. With every file and folder, you’re spreading sweetness in the world of code! 🎀  

🍒 Keep shining and remember, coding is always more magical when you sprinkle it with love and berries! 🍓💖  

[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)
