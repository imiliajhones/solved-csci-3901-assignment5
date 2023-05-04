Download Link: https://assignmentchef.com/product/solved-csci-3901-assignment5
<br>



<h1>Problem 1</h1>




Goal

Access SQL through Java.  Gain some exposure to XML.




Question

You work for the Northwind food distribution company.  Management periodically wants a summary of the company’s operation over a period of time.




Your job is to extract the summary information from the database.  You will store the summary information in a file that follows an XML format.  Someone else will then use XML tools (notably XSLT) to convert your information into something that management will review.




<h2>Input</h2>

Your program will obtain the following information from the keyboard in the following order:

<ul>

 <li>The starting date for the period to summarize</li>

 <li>The ending date for the period to summarize</li>

 <li>The name of the file for the output All dates will be in a YYYY-MM-DD format.</li>

</ul>




<h2>Output</h2>

Your program will send all of its output to the specified file.




The data that you extract will be in 3 categories:

<ol>

 <li>Customer information

  <ol>

   <li>Report the customer name, address, number of orders in the period, and total order value</li>

  </ol></li>

 <li>Product information

  <ol>

   <li>Report, for each product category, the category name and for each product in the category report the name, supplier, units sold, and value of product sold</li>

  </ol></li>

 <li>Supplier information

  <ol>

   <li>Report the supplier name, address, number of products that we sold, and the total value of business that we sold from this supplier’s products.</li>

  </ol></li>

</ol>

In all of the reporting, do not report any customers, products, or suppliers who have not had any interaction over the reporting period.




Your output file will be in an XML format.  XML uses a set of tags to surround data to let you know what the data is.  Some tags can be nested in other tags.  HTML in assignment 1 follows an XML format.




We will use a simple version of XML.  The first line of your XML file should provide information on the version of XML to use.  The following line will be sufficient:




&lt;?xml version=”1.0” encoding=”UTF-8” ?&gt;




Following this first line, we get a set of nested tags to store the data.  The starting tag has the format &lt;…&gt; and the matching ending tag has the format &lt;…/&gt; (differing by the ending slash) where … is the tag name.  The outermost tag is year_end_report




Here is a description of the correct nesting (in a data type definition (DTD) format):




&lt;!ELEMENT year_end_summary (year, customer_list, product_list, supplier_list) &gt;

&lt;!ELEMENT year (start_date, end_date) &gt;

&lt;!ELEMENT customer_list (customer*) &gt;

&lt;!ELEMENET customer (customer_name, address, num_orders, order_value) &gt;

&lt;!ELEMENT address (street_address, city, region, postal_code, country) &gt;

&lt;!ELEMENT product_list (category*) &gt;

&lt;!ELEMENT category (category_name, product*) &gt;

&lt;!ELEMENT product (product_name, supplier_name, units_sold, sale_value) &gt;

&lt;!ELEMENT supplier_list (supplier) &gt;

&lt;!ELEMENT supplier (supplier_name, address, num_products, product_value) &gt;




All items without an ELEMENT line are of type #PCDATA (if that matters to you).




As an example to read this information, the tags year_end_summary must contain nested tags for each of year, customer_list, product_list, and supplier_list.  The tag customer_list will contain zero or more tags with name “customer”, as identified by the * after the “customer” tag in the ELEMENT clause.




In an XML file, the spacing doesn’t matter.  I encourage you to use spacing and tabs to make the XML file readable by a person.




Information on XML can be found at w3schools.com.




Sample output:




&lt;?xml version=”1.0” encoding=”UTF-8” ?&gt;

&lt;year_end_summary&gt;

&lt;year&gt;

&lt;start_date&gt; 1996-01-30 &lt;/ start_date&gt;

&lt;end_date&gt; 1996-02-02 &lt;/ end_date&gt;

&lt;/year&gt;

&lt;customer_list&gt;

&lt;customer&gt;

&lt;customer_name&gt; foo &lt;/customer_name&gt;

&lt;address&gt;

&lt;street_address&gt; 123 Hemming Way &lt;/street_address&gt;

&lt;city&gt; Brandon &lt;/city&gt;

&lt;region&gt; Manitoba &lt;/region&gt;

&lt;postal_code&gt; P3J 4V2 &lt;/postal_code&gt;

&lt;country&gt; Canada &lt;/country&gt;

&lt;/address&gt;

&lt;num_orders&gt; 30 &lt;/num_orders&gt;

&lt;order_value&gt; 11425 &lt;/order_value&gt;

&lt;/customer&gt; &lt;/customer_list&gt;

&lt;product_list&gt;

&lt;category&gt;

&lt;category_name&gt; games &lt;/category_name&gt;

&lt;product&gt;

&lt;product_name&gt; game1 &lt;/product_name &gt;

&lt;supplier_name&gt; a_supplier &lt;/supplier_name&gt;

&lt;units_sold&gt; 100 &lt;/units_sold&gt;

&lt;sale_value&gt; 500 &lt;/sale_value&gt;

&lt;/product&gt;                  &lt;/category&gt;

&lt;/product_list&gt;

&lt;supplier_list&gt;

&lt;supplier&gt;

&lt;supplier_name&gt; a_supplier &lt;/supplier_name&gt;

&lt;address&gt;

&lt;street_address&gt; 456 Falcoln Ridge &lt;/street_address&gt;

&lt;city&gt; Saskatoon &lt;/city&gt;

&lt;region&gt; Saskatchewan &lt;/region&gt;

&lt;postal_code&gt; Q3C 1T8 &lt;/postal_code&gt;

&lt;country&gt; Canada &lt;/country&gt;

&lt;/address&gt;

&lt;num_products&gt; 5 &lt;/num_products&gt;

&lt;product_value&gt; 1250 &lt;/product_value&gt;

&lt;/supplier&gt;

&lt;/supplier_list&gt;

&lt;/year_end_summary &gt;





