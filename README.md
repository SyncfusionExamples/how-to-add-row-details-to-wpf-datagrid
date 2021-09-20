# How to add row details to wpf datagrid?

## About the sample

This example illustrates how to add row details to [WPF DataGrid](https://www.syncfusion.com/wpf-controls/datagrid) (SfDataGrid)?

[WPF DataGrid](https://www.syncfusion.com/wpf-controls/datagrid) (SfDataGrid) provides support to represent additional information of a row using [TemplateViewDefinition](http://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html) that can be defined in datagrid. It allows you to load any WPF controls to [TemplateViewDefinition.RowTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_RowTemplate) in order to display the additional information of a row. You can expand or collapse the row template view by using an expander in a row or programmatically.

## Defining row template

Record Template view can be generated for the rows by using the [RowTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_RowTemplate) defined in the [TemplateViewDefinition](http://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html).
	Follow the below steps to define the row template,
	•	Create [TemplateViewDefinition](http://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html).
	•	Define data template for the [TemplateViewDefinition.RowTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_RowTemplate) property.
	•	Then add [TemplateViewDefinition](http://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html) to the [SfDataGrid.DetailsViewDefinition](http://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.DetailsViewDefinition.html).
	
You can bind the row data using the Data.PropertyName (where Data is the underlying object bound)

``` Xaml

<Window.Resources>              
     <DataTemplate x:Key="DetailsViewTemplate">
         <Grid>
             <Grid.RowDefinitions>
                 <RowDefinition Height="Auto"/>
                 <RowDefinition Height="125"/>
             </Grid.RowDefinitions>
             <Grid.ColumnDefinitions>
                 <ColumnDefinition Width="250"/>
                 <ColumnDefinition/>
                 <ColumnDefinition/>
             </Grid.ColumnDefinitions>
             <Image Grid.Row="0"
                    Grid.Column="0" Grid.RowSpan="2"
                    Margin="5" Height="150"
                    HorizontalAlignment="Left" 
                    Source="{Binding Path=Data.CustomerID, Converter={StaticResource ImageConverter}}" />
             <Label Grid.Column="1" Grid.Row="0"
                    HorizontalAlignment="Left"
                    Margin="25,0,0,0"
                    Content="Order Details"
                    FontWeight="Bold" />
             <StackPanel Orientation="Vertical" Grid.Column="1" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Center">
                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Left" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Product Name :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.ProductName}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Left" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Quantity :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.Quantity}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Left" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Unit Price :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.UnitPrice, StringFormat='{}{0:C}'}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Left" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Discount :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.Discount, StringFormat='{}{0:P}'}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Left" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Freight :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.Freight, StringFormat='{}{0:c}'}"/>
                 </StackPanel>
             </StackPanel>
             <Label Grid.Column="2" Grid.Row="0"
                    HorizontalAlignment="Left"
                    Margin="25,0,0,0"
                    Content="Shipping Details"
                    FontWeight="Bold" />
             <StackPanel Orientation="Vertical" Grid.Column="2" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Center">
                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Right" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Order Date :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.OrderDate, StringFormat=d}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Right" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Shipped Date :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.ShippedDate, StringFormat=d}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Right" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Ship Address :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.ShipAddress}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Right" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Ship Postal Code :"/>
                     <TextBlock
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.ShipPostalCode, StringFormat=hh\\:mm}"/>
                 </StackPanel>

                 <StackPanel Orientation="Horizontal">
                     <Label 
                        HorizontalAlignment="Right" VerticalAlignment="Center"
                        FontWeight="SemiBold"
                        Content="Delivery Delay :"/>
                     <TextBlock 
                            HorizontalAlignment="Left"
                            VerticalAlignment="Center" Margin="5"
                            Text="{Binding Data.DeliveryDelay, StringFormat=dd\\:hh}"/>
                 </StackPanel>
             </StackPanel>
         </Grid>
     </DataTemplate>
 </Window.Resources>


<syncfusion:SfDataGrid Name="dataGrid" Margin="5" ItemsSource="{Binding OrderList}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:TemplateViewDefinition HeightMode="ViewPort" RowTemplate="{StaticResource DetailsViewTemplate}"/>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>

```

![RecordTemplateView](Images/DetailsViewTemplate_Image1.png)

## Defining RowTemplateSelector

You can to choose different DataTemplate for the record template view definitions based on underlying data object by using [TemplateViewDefinition.RowTemplateSelector](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_RowTemplateSelector) property.

```Xaml

<Window.Resources>            
    <DataTemplate x:Key="DetailsViewTemplate_WithImage">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="125"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="250"/>
                <ColumnDefinition/>
                <ColumnDefinition/>
            </Grid.ColumnDefinitions>
            <Image Grid.Row="0"
                   Grid.Column="0" Grid.RowSpan="2"
                   Margin="5" Height="150"
                   HorizontalAlignment="Left" 
                   Source="{Binding Path=Data.CustomerID, Converter={StaticResource ImageConverter}}" />
            <Label Grid.Column="1" Grid.Row="0"
                   HorizontalAlignment="Left"
                   Margin="25,0,0,0"
                   Content="Order Details"
                   FontWeight="Bold" />
            <StackPanel Orientation="Vertical" Grid.Column="1" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Center">
                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Product Name :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ProductName}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Quantity :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.Quantity}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Unit Price :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.UnitPrice, StringFormat='{}{0:C}'}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Discount :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.Discount, StringFormat='{}{0:P}'}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Freight :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.Freight, StringFormat='{}{0:c}'}"/>
                </StackPanel>
            </StackPanel>
            <Label Grid.Column="2" Grid.Row="0"
                   HorizontalAlignment="Left"
                   Margin="25,0,0,0"
                   Content="Shipping Details"
                   FontWeight="Bold" />
            <StackPanel Orientation="Vertical" Grid.Column="2" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Center">
                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Order Date :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.OrderDate, StringFormat=d}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Shipped Date :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ShippedDate, StringFormat=d}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Ship Address :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ShipAddress}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Ship Postal Code :"/>
                    <TextBlock
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ShipPostalCode, StringFormat=hh\\:mm}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Delivery Delay :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.DeliveryDelay, StringFormat=dd\\:hh}"/>
                </StackPanel>
            </StackPanel>
        </Grid>
    </DataTemplate>

    <DataTemplate x:Key="DetailsViewTemplate_WithoutImage">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="125"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition/>
                <ColumnDefinition/>
            </Grid.ColumnDefinitions>
            <Label Grid.Column="0" Grid.Row="0"
                   HorizontalAlignment="Left"
                   Margin="25,0,0,0"
                   Content="Order Details"
                   FontWeight="Bold" />
            <StackPanel Orientation="Vertical" Grid.Column="0" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Center">
                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Product Name :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ProductName}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Quantity :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.Quantity}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Unit Price :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.UnitPrice, StringFormat='{}{0:C}'}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Discount :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.Discount, StringFormat='{}{0:P}'}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Left" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Freight :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.Freight, StringFormat='{}{0:c}'}"/>
                </StackPanel>
            </StackPanel>
            <Label Grid.Column="1" Grid.Row="0"
                   HorizontalAlignment="Left"
                   Margin="25,0,0,0"
                   Content="Shipping Details"
                   FontWeight="Bold" />
            <StackPanel Orientation="Vertical" Grid.Column="1" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Center">
                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Order Date :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.OrderDate, StringFormat=d}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Shipped Date :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ShippedDate, StringFormat=d}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Ship Address :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ShipAddress}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Ship Postal Code :"/>
                    <TextBlock
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.ShipPostalCode, StringFormat=hh\\:mm}"/>
                </StackPanel>

                <StackPanel Orientation="Horizontal">
                    <Label 
                       HorizontalAlignment="Right" VerticalAlignment="Center"
                       FontWeight="SemiBold"
                       Content="Delivery Delay :"/>
                    <TextBlock 
                           HorizontalAlignment="Left"
                           VerticalAlignment="Center" Margin="5"
                           Text="{Binding Data.DeliveryDelay, StringFormat=dd\\:hh}"/>
                </StackPanel>
            </StackPanel>
        </Grid>
    </DataTemplate>
    <local:DetailsViewTemplateSelector x:Key="RecordTemplateSelector"/>
</Window.Resources>

<syncfusion:SfDataGrid Name="dataGrid" ItemsSource="{Binding OrderList}">
   
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:TemplateViewDefinition HeightMode="ViewPort" RowTemplateSelector="{StaticResource RecordTemplateSelector}" />
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>

```
![RecordTemplateView_TemplateSelector](Images/DetailsViewTemplate_Image2.png)

## Height customization

You can customize height of the row that contains [RowTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_RowTemplate) by using the [TemplateViewDefinition.HeightMode](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_HeightMode) property. 

## Populating record template view using events 

You can set the [RowTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.TemplateViewDefinition.html#Syncfusion_UI_Xaml_Grid_TemplateViewDefinition_RowTemplate) on-demand when expanding the record by using the [GridDetailsViewExpandingEventArgs.RowTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.GridDetailsViewExpandingEventArgs.html#Syncfusion_UI_Xaml_Grid_GridDetailsViewExpandingEventArgs_RowTemplate) property in [SfDataGrid.DetailsViewExpanding](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.SfDataGrid.html) event handler.

```c#

this.dataGrid.DetailsViewExpanding += DataGrid_DetailsViewExpanding;

private void DataGrid_DetailsViewExpanding(object sender, Syncfusion.UI.Xaml.Grid.GridDetailsViewExpandingEventArgs e)
{
    e.RowTemplate = GetDataTemplate();
}

private DataTemplate GetDataTemplate()
{
    FrameworkElementFactory textBlock = new FrameworkElementFactory(typeof(TextBlock));
    Binding binding = new Binding();
    textBlock.SetBinding(TextBlock.TextProperty, binding);
    binding.Path = new PropertyPath("Data.OrderID");
    var dataTemplate = new DataTemplate() { VisualTree = textBlock };
    return dataTemplate;
}

```

KB article - [How to add row details to wpf datagrid?](https://www.syncfusion.com/kb/12320/how-to-add-row-details-to-wpf-datagrid-sfdatagrid)

## Requirements to run the demo 

Visual Studio 2015 and above versions.


