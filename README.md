## How to dynamically show and hide columns on runtime with button click in Flutter DataTable?

In this article, we will show you how to dynamically show and hide columns on runtime with button click in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the required properties. You can hide and show columns using the [GridColumn.visible](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/GridColumn/visible.html) property. Set this property to false to hide the desired columns. By default, the visible property is set to true. Inside the [onChanged](https://api.flutter.dev/flutter/material/Switch/onChanged.html) callback of the [switch](https://api.flutter.dev/flutter/material/Switch-class.html) widget, update the visibility value within the setState function. This change causes the build method to run again, updating the visibility of the specified columns in the SfDataGrid.

```dart
  // To change the column's visibility.
  bool isVisible = true;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: Column(
        children: [
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              const Text('ID column'),
              Switch(
                  value: !isVisible,
                  onChanged: (value) {
                    // Update the isVisible to change the column's visibility.
                    // When toggle the switch button.
                    setState(() {
                      isVisible = !value;
                    });
                  }),
            ],
          ),
          const Padding(padding: EdgeInsets.all(5)),
          Expanded(
            child: SfDataGrid(
              source: employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: <GridColumn>[
                GridColumn(
                    visible: isVisible,
                    columnName: 'id',
                    label: Container(
                        padding: const EdgeInsets.all(16.0),
                        alignment: Alignment.center,
                        child: const Text(
                          'ID',
                        ))),
                GridColumn(
                    columnName: 'name',
                    label: Container(
                        padding: const EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: const Text('Name'))),
                GridColumn(
                    columnName: 'designation',
                    label: Container(
                        padding: const EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: const Text(
                          'Designation',
                          overflow: TextOverflow.ellipsis,
                        ))),
                GridColumn(
                    columnName: 'salary',
                    label: Container(
                        padding: const EdgeInsets.all(8.0),
                        alignment: Alignment.center,
                        child: const Text('Salary'))),
              ],
            ),
          ),
        ],
      ),
    );
  }
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-dynamically-show-and-hide-columns-on-runtime-in-Flutter-DataTable).