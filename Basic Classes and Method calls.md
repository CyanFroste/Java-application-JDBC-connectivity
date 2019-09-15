### Note : Mostly Operations on JFrame form

## JOptionPane
```
JOptionPane.showMessageDialog(this, " - your message here - ");
```
```
int Choice = JOptionPane.showConfirmDialog(null, "Delete?","Warning", JOptionPane.YES_NO_OPTION);
```

## JTextfield
```
Jtextfield_name.getText();
```
```
Jtextfield_name.setText(" ");
```
```
Jtextfield_name.requestFocus();
```
```
int Value = Integer.parseInt(Jtextfield_name.getText());
```
```
float Value = Float.parseFloat(Jtextfield_name.getText());
```
```
Jtextfield_name.getText() = String.valueOf(Object);
```

## JCombobox
- Inserting an Object into a combobox

```
private class CategoryItem{
    int id;
    String name;
    public CategoryItem(int id, String name){
        this.id = id;
        this.name = name;
    }        
    @Override
    public String toString(){
        return name;
    }
}

// Adding the Object into the Jcombobox
JCombobox_name.addItem(new CategoryItem(ID, name ));

// Displaying the Object that's in the JCombobox's list
JCombobox_name.getModel().setSelectedItem(new CategoryItem(ID, name));
```
- If the Object is just a string
```
JCombobox_name.addItem("Name");
```
```
JCombobox_name.setSelectedItem("Name");
```

## JSpinner
- stateChange event
```
String Value = JSpinner_name.getValue().toString();
```
```
int Value = Integer.parseInt(JSpinner_name.getValue().toString());
```
- Remodelling a JSpinner to visually change its value (zero here)
```
JSpinner_name.setModel(new SpinnerNumberModel(0, 0, null, 1));

JSpinner_name.setEditor(new JSpinner.NumberEditor(JSpinner_name, "");
```

## JTable
- Reading from a table using Mouseclick event
```
// getting table model
DefaultTableModel model = (DefaultTableModel)JTable_name.getModel();
```
```
// selecting a row with mouseclick event
int Index = JTable_name.getSelectedRow();
```
```
// getting value at the zeroth column
model.getValueAt(Index, 0).toString()
```
- Writing onto a table
```
model.addRow(new Object[]{
    value 1,
    value 2,
    value 3,
    value 4
} );
```

```
int ColumnCount = model.getColumnCount();
```
```
model.setRowCount(RowCount);
```

## Dispose Current form and Create New form instance

```
New_Form's_Class_name MainClass = new New_Form's_Class_name();
        this.dispose();
        MainClass.setVisible(true);
```

## Getting KeyCode inside  Key Press/Released/Typed  events
```
if(evt.getKeyCode() == KeyEvent.VK_ENTER){     
    
     // VK_UNDEFINED FOR ANY KEY

    - Code here -
}
```

## Customizing JTable
- Setting Header Font
- cell font can be changed in Netbeans
```
JTable_name.getTableHeader().setFont( new Font( font_name , Font.PLAIN, font_size ));
```

- Aligning Table - CENTER
```
DefaultTableCellRenderer center = new DefaultTableCellRenderer();        
center.setHorizontalAlignment(DefaultTableCellRenderer.CENTER);

int cc = JTable_name.getModel().getColumnCount();
        for(int i=0; i<cc; i++){
            JTable_name.getColumnModel().getColumn(i).setCellRenderer(center);
        }
DefaultTableCellRenderer renderer = (DefaultTableCellRenderer)JTable_name.getTableHeader().getDefaultRenderer();

renderer.setHorizontalAlignment(JLabel.CENTER);
```

