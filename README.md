# Quick Python Printf

## Installation

Several places to install this from:
- [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=MihaiCosma.quick-python-printf)
- Search "Quick-Python-Printf" in the plugin tab of Visual Studio Code.

works on vscode version ≥ 1.57.0.

## Motivation

This extension is inspired by "[Quick Python Print](https://github.com/wwdok/Quick-Python-Print)". 

The only differnece is this extension uses `print(f"{variable=}")` instead of `print("variable",variable)`.

"Quick Quick Print" can quickly print out variables on the console by using shortcut `Ctrl+Shift+L`, while "Quick Python Print" enhances some features:
* You can put the cursor at target line, the extension will automatically recognize the variable in the line.
* If did not recognize any variable in current line, it will just insert simply `print()` and move the cursor inside the bracket.
* Press `Ctrl+Shift+O` to print out tensor shape by default, e.g. `print("==>> a.shape: ", a.shape)`.
* Press `Ctrl+Shift+T` to print out variable type by default, e.g. `print("==>> type(a): ", type(a))`.
* Press `Ctrl+Shift+;` to insert `print("".center(50, "-"))` used for printing delimiter line.
* Press `Ctrl+Shift+/` to comment out or uncomment all print statement inside the selection or in the file.
* Press `Ctrl+Shift+R` to delete all print statements inside the selection or in the file.
* Allow user to define customized prefix and suffix of print content flexibly in extension settings.
* Able to output colored text in terminal by using python built-in package: `termcolor`.

If you find bug or have feature request, you can check out the ChangeLog to see if this bug or feature had been fixed or added in latest version, if not, please issue it in this extension's [github repo](https://github.com/wakamex/Quick-Python-Print).

## How to use

Introduction video: [Bilibili](https://www.bilibili.com/video/BV1hY411V7bi) | [Youtube](https://www.youtube.com/watch?v=w5cd_8lzylA) (When I made this video, it was version 0.1.1, and there have been many changes in the current version).

This extension only activates within `.py` and `.ipynb` files.

### Keyboard Shortcut
For Mac user, the `Ctrl` should be `Cmd`.

**Ctrl+Shift+L**

Select the variable, then press `Ctrl+Shift+L`, it will insert print statement at next line:

![](images/Ctl+Shift+L-selection.gif)

You can also just put the cursor at the target line, then the extension will automatically recognize the variable before `=` or `+=` or the unpacked variables separated by `,`:

![](images/Ctl+Shift+L-NOselection.gif)

If you didn't select variable or the extension can't recognize variable, it will just insert simply print() and move the cursor inside it. If selected variable is new defined for the first time, insert code at current line :

![](images/Ctl+Shift+L-NOvariable.gif)

If the extension recognize variable wrongly, you can manually select the variable, or report this issue in github repo.

**Ctrl+Shift+O**

`Ctl+Shift+O` is similar to `Ctrl+Shift+L` except that it will print tensor shape by default:

![](images/Ctl+Shift+O.gif)

**Ctrl+Shift+T**

`Ctl+Shift+T` is similar to above except that it will print type of variable by default:

![](images/Ctl+Shift+T.gif)

**Ctrl+Shift+/**

Comment out or uncomment the print statement in the selected scope or in the python file:

![](images/Ctl+Shift+forwardslash.gif)

**Ctrl+Shift+Up**

Comment out all print statement above the cursor in the python file:

![](images/Ctl+Shift+up.gif)

**Ctrl+Shift+Down**

Comment out all print statement below the cursor in the python file:

![](images/Ctl+Shift+down.gif)

**Ctrl+Shift+;**

Insert a print statement that will print 50 `-` to form a delimiter like `--------------------------------------------------`:

![](images/Ctl+Shift+;.gif)

**Ctrl+Shift+R**

Delete all the print statement(include those commented) in the python file or in the selected scope:

![](images/Ctl+Shift+R.gif)

**Compatibility with different framework**

Many deep learning framework all have `.shape` attribute of tensor:

![](images/execution.gif)

If any of these shortcuts conflicts with existing shortcut, you may change it in the `Keyboard Shortcuts Setting`: Press `Cmd+P` or `Ctrl+P` and type in `>Open Keyboard Shortcuts`. Search for the conflict shortcut, then you will find those shortcut using the same keys, then right click one of them, modify or delete keybinding.

### Extension Settings

This extension has following settings:

![](images/setting1.png)
![](images/setting2.png)

You can go to the `Extension Settings` to modify them to suit your preferences. After modification, it should take effect immediately.

### Color output text
To color the output text in terminal, you need to do these things:
1. Go to `Extension Settings`, check the `5.enable-colored-output-text` to be true. And you can select the color you like from the drop-down list.
2. Add `from termcolor import colored` in the python file
3. Now Press `Ctrl+Shift+L` or `Ctrl+Shift+O` or `Ctrl+Shift+T` will insert the print statement that can color output text.
4. Run Python File in Terminal.

![](images/color-text.gif)

## pypi package
I also make a pypi package : [printensor](https://github.com/wwdok/print_tensor) to uppack tensors inside list, tuple, dict, generator, then print their tensor shape. After installing and import, you can replace `print(` with `prints(` to intergrate it with this extension.

## Known issue
This extension can not handle tensor that cross multiple lines, for example:
```
a = torch.tensor([[1.0, 2.0, 3.0], 
                [4.0, 5.0, 6.0]])
```
You can use `Alt + down` to move down the inserted print statement.

## License
MIT License
