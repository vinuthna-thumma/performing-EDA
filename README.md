# performing-EDA
It is a kind of a small project on data analysis, where i have done some sort of EDA as required and extracted the information needed. by using the python and the pandas library
The following are some queries on which i have worked on.
<h3>1.List all the cities and the respective number of pending orders in “India”?</h3>
•	x=df[(df["Order Country"]=="India") & (df["Order Status"]=="PENDING")] 
•	print(f"number of pending orders with respect to cities\n", x[x['Order Status']=="PENDING"]['Order City'].value_counts()) 
<h3>2.Which country had the most suspected fraud?</h3>
•	highfraud=df[(df['Order Status']=='SUSPECTED_FRAUD')&(df['Type']=='TRANSFER')]
•	valuecounts=highfraud["Order Region"].value_counts()
•	highfraud["fraudcounts"]=highfraud["Order Region"].map(z1)
•	highfraud.sort_values("fraudcounts").tail(1)

<h3>3.Which year had the minimum sales for the “Nike” product?</h3>
•	df['order_year']= pd.DatetimeIndex(df['order date (DateOrders)']).year  
•	df2=df[['order_year','Sales','Product Name']]
•	df2=df2[df2['Product Name'].str.contains("Nike")]
•	df2[['Sales','order_year','Product Name']].value_counts()
•	result_df=c[(df2['Sales']==df2['Sales'].min()) & df2['order_year']]
•	result_df[['order_year']].value_counts()

<h3>4.Which product(s) has/have the maximum discount?</h3>
•	df["Order Item Discount"].max()
•	dis=df.sort_values('Order Item Discount')
•	print(f"This Product has the maximum Discount----",dis["Product Name"].tail(1))

<h3>5.How many successfully processed orders have days for shipping (real) >Days for shipping (Scheduled) ?</h3>
<li><ul>	df=df.rename(columns={"Days for shipping (real)":"Real_shipping","Days for shipment (scheduled)":"Scheduled_shipping"})</ul>
	<ul>late_df=df[((df["Real_shipping"])>(df["Scheduled_shipping"]))&(df["Order Status"]=="COMPLETE")].</ul>
  <ul>late_df=late_df[["Real_shipping","Scheduled_shipping","Order Status"]].</ul>
  <ul>late_df.shape[0]</ul></li>
