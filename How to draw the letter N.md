# How to draw the letter N
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2013/02/18/draw-letter-n/
```PowerShell
#Create pen
$mypen = new-object Drawing.Pen red
$mypen.width = 10

$form = New-Object Windows.Forms.Form
$form.Width = 500
$form.Height = 550
$formGraphics = $form.createGraphics()

#N
$form.add_paint({$formGraphics.DrawLine($mypen, 0, 0, 200, 200)})

$form.add_paint({$formGraphics.DrawLine($mypen, 0, 0, 0, 200)})
$form.add_paint({$formGraphics.DrawLine($mypen, 200, 0, 200, 200)})

$form.ShowDialog()

```
