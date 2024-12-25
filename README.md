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
🐦 **X (formerly Twitter)**: [@LucyBerryHub](https://x.com/lucyberryhub)  
📸 **Instagram**: [LucyBerryHub](https://instagram.com/lucyberryhub)  
📘 **Facebook Group**: [LucyBerry Coding Hub](https://www.facebook.com/groups/lucyberry)


# Lucy Berry's Sweet Coding Recipe Book

| **Section**                                          | **Description**                                                         |
|------------------------------------------------------|-------------------------------------------------------------------------|
| [🍒**Cherry Berry File Handling & JSON Jar Magic**](#file-handling--json-jar-magic---a-lovely-girly-guide)| A Lovely JSON File Handling Guide|
| [🍒**Fixing the ColorDialog**](#fixing-the-colordialog)| Learn how to fix and customize the ColorDialog in a fun and sweet way! |
| [🍒**DockPanel, Grid, and StackPanel**](#dockpanel-grid-and-stackpanel)| Berry-Sweet Layout Magic in WPF: DockPanel, Grid, and StackPanel Explained! 🍓✨ |
| [🍒**Cherry Berry Color Picker** 🍓](#cherry-berry-color-picker)| Create the color picker by building it with a **WrapPanel** full of berry squares |
---



## File Handling & JSON Jar Magic - A Lovely, Girly Guide!
[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)

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

### **Conclusion: You're a Lucy Berry Star!** 🍓✨  
Congratulations, darling! 💖 You’ve just created the cutest **JSON jar system** ever. With every file and folder, you’re spreading sweetness in the world of code! 🎀  

---  



## Fixing the ColorDialog
[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)

Welcome to **Lucy Berry's Berry Sweet Tutorial**! 🌸💖 Today, we’ll fix that pesky problem with your `ColorDialog` hiding behind your window! But don’t worry, we’re going to make sure the dialog always pops up like a *delicious cherry on top* 🍒. Let’s go ahead and *berry-fy* your code! 🍓✨

---

### 🍓 Problem: The ColorDialog Is Hiding Behind 🍒

Oh no! 😱 Your `ColorDialog` is hiding behind your WPF window like a shy berry in a basket, and we want to bring it to the front! 🍒 So, let's use a little *berry magic* to make it always appear on top. 🌟

---

### 🍒 What We'll Do

We’ll temporarily make your window the **TopMost** (like placing a cherry on top of a cupcake!) so that the `ColorDialog` can *shine brightly in front of your WPF window*. 🍓🌈

---

### 💖 Step 1: Add Some Berry Magic to Bring the ColorDialog to the Front

Now, let’s make your WPF window *TopMost* like a cherry on top of a *berry* sundae! 🍒🍓 Here's how we'll do it:

```csharp
// 🍓🍒 Sweet ColorDialog Fix for Lucy Berry 🍒🍓
private void OnBerryColorClicked(object sender, RoutedEventArgs e)
{
    // Show the ColorDialog like a sweet berry burst! 🍓
    var colorDialog = new System.Windows.Forms.ColorDialog();

    // Find the WPF window where the ColorDialog will show up
    var berryWindow = Window.GetWindow(this);

    if (berryWindow != null)
    {
        // Temporarily make the berry window *TopMost* (like a cherry on top!)
        bool wasTopMost = berryWindow.Topmost;
        berryWindow.Topmost = true;

        // Activate the berry window to bring it to the front
        berryWindow.Activate();

        // Use WindowInteropHelper to get the native window handle
        var berryHelper = new System.Windows.Interop.WindowInteropHelper(berryWindow);
        
        // Wrap the window handle with our NativeBerryWindow class
        var ownerBerryWindow = new NativeBerryWindow(berryHelper.Handle);

        // Display the ColorDialog with the berry window as the owner
        var berryResult = colorDialog.ShowDialog(ownerBerryWindow);

        // If the user picks a color, update the berry color
        if (berryResult == System.Windows.Forms.DialogResult.OK)
        {
            Color selectedBerryColor = ColorFromArgb(colorDialog.Color);
            UpdateBerryColor(selectedBerryColor);
        }

        // After the dialog is closed, restore the berry window's original TopMost state
        berryWindow.Topmost = wasTopMost;
    }
    else
    {
        // If no berry window is found, show the ColorDialog anyway
        var berryResult = colorDialog.ShowDialog();
        if (berryResult == System.Windows.Forms.DialogResult.OK)
        {
            Color selectedBerryColor = ColorFromArgb(colorDialog.Color);
            UpdateBerryColor(selectedBerryColor);
        }
    }
}
```

---

### 🍒 Step 2: Add the Sweet NativeBerryWindow Class 🍓

Now, let’s define our *NativeBerryWindow* class so we can pass the native window handle to the `ColorDialog`. This will help keep the dialog in front of your window, like the juiciest berry in the patch! 🍒🍓

```csharp
// 🍓🍒 NativeBerryWindow Class 🍒🍓
public class NativeBerryWindow : IWin32Window
{
    public NativeBerryWindow(IntPtr berryHandle)
    {
        Handle = berryHandle;
    }

    public IntPtr Handle { get; private set; }
}
```

---

### 🍓 Explanation: How It Works 🍒

1. **Temporary TopMost**: We make the window *TopMost* by setting `berryWindow.Topmost = true;` to bring it forward. 🍒 Like placing your favorite berry on top of your dessert! 🍓
2. **Activate the Window**: We use `berryWindow.Activate();` to make sure the window is brought into focus (just like *shining* a spotlight on your berry!). 🌟
3. **Dialog Shows Up**: We pass the `NativeBerryWindow` to the `ColorDialog` to make sure it shows up in front. 🍒✨

---

### 🍓💖 Bonus Step: Make Your UI Even More Berry-licious! 🍒🍓

Now, let’s make everything *extra cute* by adding emojis and *berry magic* to your UI. 🍓🍒 We want your user interface to be as sweet as your favorite berry tart! 🌸🍓

---

### 🌸 Conclusion: You Did It, Sweet Berry! 🍓

Yay! 🎉🍒 You’ve successfully fixed the `ColorDialog` issue and made it pop up in front of your window like the juiciest cherry on top of a berry parfait! 🍓🌟 Now your app is even *more berry sweet* than ever! 🍒🍓

Remember, coding can be just as fun as a berry-picking adventure, and you’ve done a wonderful job, Lucy Berry! 🍓✨

---

### 🍒🍓 GitHub Fun: Cherry Emoji Power! 🍓🍒

Here's a *berry sweet* example for your GitHub repo:

```markdown
🍓💖 Lucy Berry’s Sweet Tutorial 🍓💖
- 🍒 **Berry ColorDialog Fix**: Make the dialog pop up on top like a cherry on top! 🍒
- 🍓 **Berry Magic**: Smoothly bring the dialog forward! 🍓
```


**"Berry-Sweet Layout Magic in WPF: DockPanel, Grid, and StackPanel Explained! 🍓✨"**
## DockPanel Grid and StackPanel
[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)
---

### 1. **DockPanel: The Berry Border Queen 🍓👑**
Imagine laying out your cute cherries and strawberries around the edges of a plate, leaving the middle for the juiciest berry treat! That’s our DockPanel—she loves to dock her friends to the **top, bottom, left, or right**. 🍒✨

- **Key Traits**:
  - Snuggles her friends to the edges. 🍓
  - The last child gets to chill in the leftover space, like a big cherry surprise. 🍒✨
  - Use `DockPanel.Dock` to tell her where to dock each cutie.

**Berry Example**:
```xml
<DockPanel LastChildFill="True">
    <Button Content="Top Berry 🍓" DockPanel.Dock="Top" />
    <Button Content="Left Cherry 🍒" DockPanel.Dock="Left" />
    <Button Content="Center Treat 🍰" />
</DockPanel>
```

💖 **Best For**: Toolbars, sidebars, and layouts with cute corners.  
🌟 **Berry Pro**: Super simple for edgey cuteness!  
🍬 **Cherry Con**: Not for fancy grid vibes.

---

### 2. **Grid: The Organized Cherry Boss Babe 🍒📊**
The **Grid** is like the sassy berry boss who organizes her space into perfect little cherry boxes. Rows, columns—she’s got it all, darling! 💼✨ She’s all about precision, and she makes sure every berry is perfectly placed. 🍓

- **Key Traits**:
  - Divides space into rows and columns. 🧺✨
  - Lets you combine boxes for big cherry cakes (`RowSpan` & `ColumnSpan`). 🍰
  - Perfect for when you need total berry control!

**Berry Example**:
```xml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="200" />
    </Grid.ColumnDefinitions>

    <Button Content="Top Cherry 🍒" Grid.Row="0" Grid.ColumnSpan="2" />
    <Button Content="Berry Left 🍓" Grid.Row="1" Grid.Column="0" />
    <Button Content="Right Treat 🎂" Grid.Row="1" Grid.Column="1" />
</Grid>
```

💖 **Best For**: Complex berry-tiful layouts like forms and dashboards.  
🌟 **Berry Pro**: Total control over cherry positions!  
🍬 **Cherry Con**: A bit more work for simple cutie layouts.

---

### 3. **StackPanel: The Chill Cherry Stack Queen 🍒🍰**
StackPanel is your go-to for a quick stack of cherry cupcakes or a line of strawberries! 🌈 She’s sweet and simple, arranging all the goodies in a straight line—either **vertical** or **horizontal**. 💅✨

- **Key Traits**:
  - Stacks items one after another. 🎀
  - Loves her linear berry vibes. 🍓
  - Set `Orientation` to `Vertical` or `Horizontal`.

**Berry Example**:
```xml
<StackPanel Orientation="Vertical">
    <Button Content="Berry 1 🍓" />
    <Button Content="Berry 2 🍓" />
    <Button Content="Cherry on Top 🍒" />
</StackPanel>
```

💖 **Best For**: Menus, lists, and simple layouts.  
🌟 **Berry Pro**: Sooo easy and breezy! 🍓  
🍬 **Cherry Con**: Can’t handle super structured layouts.

---

### Berry-Sweet Comparison Table! 🍓✨

| **Feature**              | **DockPanel 🍓**               | **Grid 🍒**                              | **StackPanel 🍰**               |
|--------------------------|-------------------------------|------------------------------------------|---------------------------------|
| **Style**                | Berry border queen 🍓         | Boss babe cherry boxes 📊🍒              | Chill berry stack vibes 🍓🍰      |
| **Flexibility**          | Moderate 🍬                   | High 🍒                                  | Low 🎀                          |
| **Complexity**           | Simple 🍓                     | Fancy 🍒✨                               | Super simple 🍰                 |
| **Best For**             | Edgey cuteness 🍒🍓           | Precision cherry layouts 📊✨            | Stacked treats 🍓🍒             |

---

### Berry Conclusion! 🍓✨
- **DockPanel**: Perfect for when your layout is all about the edges. 🍒  
- **Grid**: Your go-to for classy, structured cherry goodness. 🍓  
- **StackPanel**: Sweet and simple for stacking cute berries. 🍰  

Choose your berry-best layout and let those cherries shine! 🌸✨





## Cherry Berry Color Picker
[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)

Welcome to the **Cherry Berry Color Picker**! 🍒🍓 Today, Lucy learned how to create an adorable and efficient color picker. This color picker uses a beautiful cherry and berry theme with rounded squares as a palette, perfect for picking colors in a sweet and stylish way! 🌸💖

## 🍓 Features

- **Color Palette:** A collection of delightful cherry and berry-inspired colors to choose from 🍒🍓
- **Easy to Use:** Smooth and easy-to-navigate interface with cute rounded squares 🍬
- **Cute and Playful:** The perfect blend of fun colors and berry-themed icons to brighten up your day 🌈✨

## 🍒 How Lucy Learned It 🍓

Lucy learned how to create the color picker by building it with a **WrapPanel** full of berry squares. Each square represents a color in a playful and rounded shape, just like juicy cherries and berries! Here's how you can build your own version! 🍒🍓

### 🍓 XAML Code

```xml
<StackPanel x:Name="BerryTab" Visibility="Visible" Margin="10" Background="White">
    <TextBlock Text="🍒 Cherry Berry Palette 🍓" FontWeight="Bold" Margin="0,10,0,5" />
    <WrapPanel x:Name="BerryWrapPanel" HorizontalAlignment="Left" >
        <!-- Color Palette (Berry and Cherry colors) -->
    </WrapPanel>
</StackPanel>
```

### 🍒 C# Code

```csharp
private void LoadBerryColors()
{
    // Initialize the color list with some berry-inspired colors
    _berryColors = new ObservableCollection<string>
    {
        "CherryRed", "BlueberryBlue", "StrawberryPink", "RaspberryRed", "GrapePurple", "PeachOrange", "BlackberryBlack"
    };

    BerryWrapPanel.Children.Clear(); // Clear previous berry squares
    int itemsInRow = 7; // Number of berry squares per row
    int berryCount = 0; // Track the number of berry squares in the current row

    // Load initial Berry Colors
    LoadBerryItems(_berryColors, ref berryCount, itemsInRow);

    // Load colors dynamically from the ViewModel (More Berries!)
    var berryColorsFromJson = viewModel.GetBerryColorsFromJson();
    LoadBerryItems(berryColorsFromJson.Select(c => c.Color).ToList(), ref berryCount, itemsInRow);

    // Add the "Add Berry" button 🍒
    AddBerryButton();
}

private void LoadBerryItems(IEnumerable<string> berryColors, ref int berryCount, int itemsInRow)
{
    foreach (var color in berryColors)
    {
        // Create and configure the berry square
        var berrySquare = CreateBerrySquare(color);

        // Add the berry square to the panel
        BerryWrapPanel.Children.Add(berrySquare);
        berryCount++;

        // If we've reached the maximum number of berry squares in a row, start a new row
        if (berryCount % itemsInRow == 0)
        {
            BerryWrapPanel.Children.Add(new UIElement()); // Empty space for next row
        }
    }
}

private UIElement CreateBerrySquare(string color)
{
    var berrySquare = new Border
    {
        Width = 30,
        Height = 30,
        Background = new SolidColorBrush((Color)ColorConverter.ConvertFromString(color)),
        BorderBrush = Brushes.Gray,
        BorderThickness = new Thickness(1),
        Margin = new Thickness(2),
        CornerRadius = new CornerRadius(5) // Rounded corners like sweet berries!
    };

    // Add a tooltip to show the berry color name 🍓
    berrySquare.ToolTip = $"{color} Berry";

    // Attach MouseDown event for berry color selection 🍒
    berrySquare.MouseDown += OnBerryColorSelected;

    return berrySquare;
}

private void AddBerryButton()
{
    var addBerryButton = new Button
    {
        Content = "🍓 Add Berry 🍒",
        Background = new SolidColorBrush(Colors.Pink),
        BorderBrush = new SolidColorBrush(Colors.White),
        Width = 30,
        Height = 30,
        Margin = new Thickness(2),
        HorizontalAlignment = System.Windows.HorizontalAlignment.Left
    };

    addBerryButton.Click += OnAddBerryColorClicked;
    BerryWrapPanel.Children.Add(addBerryButton);
}
```

## 🍒 Functions & Keywords 🍓

- **LoadBerryColors:** This is where we fill the palette with our delicious berry colors, including cherry red and blueberry blue 🍒🍓
- **LoadBerryItems:** Loads each berry square dynamically into the WrapPanel, just like arranging your berry basket 🫐🍓
- **CreateBerrySquare:** Turns each color into a cute, rounded berry square 🍒
- **AddBerryButton:** Adds a fun button to let users add their own custom berry colors 🍇

## 🍓 Contribution Guidelines

🍒 If you want to add more colors or enhance the berry experience, please feel free to fork this repo and submit your pull requests. We love contributions that bring more sweetness to our berry world! 🍇🍓

- **Add New Berry Colors:** Add new fruit-inspired colors to the palette!
- **Berry Theme Enhancements:** Improve the UI with more cherry and berry-themed elements 🫐

## 🍒 How to Run

To try out the **Cherry Berry Color Picker**:

1. Clone this repository.
2. Open the solution in Visual Studio (or your favorite IDE).
3. Build and run the application.
4. Enjoy picking your favorite berry-inspired colors! 🍓🍒

---


## How to Delete the Selected Berry from the JSON File
[Back to Contents](#lucy-berrys-sweet-coding-recipe-book)

Welcome to the tutorial of the day where we learned how to delete a selected **berry** from the JSON file! 🍇🍓✨ This tutorial is full of **cherry** icons, cutie girly stuff, and a lot of fun. 🍒

We will guide you through the steps involved in creating a color picker (with berry themes!) and how to delete a color from the JSON file when selected. 💖

## 💫 **Features**:

- **Color Selection**: You can pick from a variety of delicious berry-colored squares 🍒🍓.
- **Add a Berry**: Add a custom berry color to the picker! 🍓
- **Delete a Berry**: Delete any berry color directly from the list! 🍒

## 🍒 **How the Code Works**:

### 1. **Initializing the Cherry Color Picker** 🍓

When the cherry color picker is created, it loads an initial list of berry colors 🍇🍒 from a predefined set.

```csharp
public partial class CherryBerryPicker : UserControl
{
    private ObservableCollection<BerrySettingModel> _berryColors;

    // Selected Berry Dependency Property
    public static readonly DependencyProperty SelectedBerryProperty =
        DependencyProperty.Register("SelectedBerry", typeof(Color), typeof(CherryBerryPicker), new PropertyMetadata(Colors.Transparent));

    public Color SelectedBerry
    {
        get { return (Color)GetValue(SelectedBerryProperty); }
        set { SetValue(SelectedBerryProperty, value); }
    }

    public CherryBerryPicker()
    {
        InitializeComponent();
        LoadBerryColors(); // Loading the initial berry colors!
    }

    private void LoadBerryColors()
    {
        _berryColors = new ObservableCollection<BerrySettingModel>
        {
            new BerrySettingModel { Id = 1, BerryColor = "BlackBerry", IsFromJson = false },
            new BerrySettingModel { Id = 2, BerryColor = "BlueBerry", IsFromJson = false },
            new BerrySettingModel { Id = 3, BerryColor = "StrawBerry", IsFromJson = false },
            new BerrySettingModel { Id = 4, BerryColor = "RedBerry", IsFromJson = false },
            new BerrySettingModel { Id = 5, BerryColor = "GreenBerry", IsFromJson = false },
            new BerrySettingModel { Id = 6, BerryColor = "YellowBerry", IsFromJson = false }
        };

        BerryWrapPanel.Children.Clear(); // Clear old berry items
        int itemsInRow = 5; // Set number of berry items per row
        int itemCount = 0;

        // Load the berry colors
        LoadBerryItems(_berryColors, ref itemCount, itemsInRow);

        // Dynamically add berries from the berry database
        var berries = GetBerriesFromJson();
        foreach (var berry in berries)
        {
            berry.IsFromJson = true; // These berries are from JSON
        }
        LoadBerryItems(berries, ref itemCount, itemsInRow);

        // Add the "Add Berry" button!
        AddAddBerryButton();
    }

    private void LoadBerryItems(IEnumerable<BerrySettingModel> berries, ref int itemCount, int itemsInRow)
    {
        foreach (var berry in berries)
        {
            // Create the berry item (Berry Square)
            var square = CreateBerrySquare(berry);

            // Add the berry item to the panel
            BerryWrapPanel.Children.Add(square);
            itemCount++;

            // If we've hit the max items per row, add a new row
            if (itemCount % itemsInRow == 0)
            {
                BerryWrapPanel.Children.Add(new UIElement()); // Empty space for next row
            }
        }
    }
```

### 2. **Creating Berry Square Button** 🍇🍓

Each berry color is displayed as a clickable square. If it’s a **cherry berry** from JSON, we add a delete option.

```csharp
private UIElement CreateBerrySquare(BerrySettingModel berryModel)
{
    var button = new Button
    {
        Background = new SolidColorBrush((Color)ColorConverter.ConvertFromString(berryModel.BerryColor)),
        Margin = new Thickness(2),
        ToolTip = $"{berryModel.BerryColor} ({berryModel.Id})",
        Style = (Style)FindResource("RoundButtonStyle"),
        Tag = berryModel.Id // Tag the button with the berry Id
    };

    // If the berry is from JSON, add delete option
    if (berryModel.IsFromJson)
    {
        var contextMenu = new ContextMenu();
        var deleteMenuItem = new MenuItem { Header = "Delete Berry" };

        // Add the delete icon
        var deleteIcon = new Image
        {
            Source = (ImageSource)FindResource("DeleteBerryIcon"),
            Width = 16,
            Height = 16
        };

        deleteMenuItem.Icon = deleteIcon;

        // Add click handler for the delete berry
        deleteMenuItem.Click += (s, e) => OnBerryDelete(button);
        contextMenu.Items.Add(deleteMenuItem);
        button.ContextMenu = contextMenu;
    }

    // Attach MouseDown event for berry selection
    button.Click += (s, e) => OnBerrySelected(button);

    return button;
}
```

### 3. **Delete the Selected Berry** 🍓🍒

When a user selects a berry, the `OnBerryDelete` method is triggered. It deletes the berry from the JSON file and removes the UI item.

```csharp
private void OnBerryDelete(Button button)
{
    if (button.Tag is long berryId)
    {
        var berryFilePath = "berries.json"; // Path to the berry JSON file

        // Step 1: Read the current berry data
        var jsonData = File.ReadAllText(berryFilePath);

        // Step 2: Deserialize to list of BerrySettingModels
        var berrySettings = JsonConvert.DeserializeObject<List<BerrySettingModel>>(jsonData);

        if (berrySettings != null)
        {
            // Step 3: Find and remove the selected berry
            var berryToRemove = berrySettings.FirstOrDefault(x => x.Id == berryId);
            if (berryToRemove != null)
            {
                berrySettings.Remove(berryToRemove);
                var updatedJsonData = JsonConvert.SerializeObject(berrySettings, Formatting.Indented);
                File.WriteAllText(berryFilePath, updatedJsonData);
            }
        }

        // Remove the berry from the UI
        if (button.Parent is Panel parentPanel)
        {
            parentPanel.Children.Remove(button);
        }
    }
}
```

### 4. **Handling Berry Selection** 🍒

When a berry is clicked, we raise an event to notify the app about the selected berry color.

```csharp
private void OnBerrySelected(Button button)
{
    if (button.Background is SolidColorBrush brush)
    {
        Color selectedBerryColor = brush.Color;
        // Notify about the selected berry color
        BerrySelected?.Invoke(selectedBerryColor);
    }
    else
    {
        MessageBox.Show("Couldn't select the berry.");
    }
}

public event Action<Color> BerrySelected;
```

### 5. **Add Custom Berry Color** 🍇🍒

A "Add Berry" button is added that lets users pick their custom berry color and save it to the list.

```csharp
private void OnCustomBerryClicked(object sender, RoutedEventArgs e)
{
    var berryDialog = new System.Windows.Forms.ColorDialog();
    var parentWindow = Window.GetWindow(this);

    if (parentWindow != null)
    {
        parentWindow.Topmost = true;
        var helper = new System.Windows.Interop.WindowInteropHelper(parentWindow);
        var ownerWindow = new NativeWindowWrapper(helper.Handle);

        var result = berryDialog.ShowDialog(ownerWindow);

        if (result == System.Windows.Forms.DialogResult.OK)
        {
            Color selectedBerryColor = ColorFromArgb(berryDialog.Color);
            UpdateSelectedBerryColor(selectedBerryColor);
        }

        parentWindow.Topmost = false;
    }
}
```

## 💖 **Conclusion**:

You now know how to delete the selected berry from the JSON file and work with colors in your app! 🍇🍒 Add new colors, delete existing ones, and select your favorite berry color! 🌸 

Enjoy coding with the sweetest berry colors! 💖🍓

### 🍒 **Remember**: Always be sweet and juicy like berries in your code! 🍓


### Key Highlights:
- Renamed methods and variables with berry and cherry-related terms (e.g., `BerrySettingModel`, `CreateBerrySquare`, `OnBerryDelete`, etc.).
- Cleaned up the `viewModel` code and integrated all methods directly into the `CherryBerryPicker` class.
- The **Add Berry** and **Delete Berry** features now handle berries instead of colors.

Hope this adds a fun touch to your project! 🍓🍒



**🍒 Made with love and berries by Lucy! 🍓**
---
### 💖 Keep Coding and Stay Berry Sweet! 💖

Thanks for joining me on this *berry* sweet journey! 🍓🍒 I hope this tutorial was as fun as a basket full of cherries 🍒 and berries 🍓! Stay cute, stay *berry* sweet, and always make your code as fabulous as a fruit salad! 🍓💖
