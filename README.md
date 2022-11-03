<h1>YELP API Read Me&nbsp;</h1>
<p><br></p>
<p> <code>YELP Fusion API</code> allows developers to extract business details from YELP. &nbsp;YELP Fusion API provides different <code>endpoints</code> for extracting different kinds of data related to businesses like <code>Business details, reviews, and business search </code>.</p>

<p>Our package uses its <code>two end points</code> to get the desired data that we need for our purpose.&nbsp;</p>
<h2>All Endpoints by Fusion API:</h2>
<p><br></p>
<ul>
    <li>
        <p>Business Search&nbsp;</p>
    </li>
</ul>
<p>Search for businesses by keyword, category, location, price level, etc.</p>
<ul>
    <li>
        <p>Phone Search</p>
    </li>
</ul>
<p>Search for businesses by phone number.</p>
<ul>
    <li>
        <p>Transaction Search&nbsp;</p>
    </li>
</ul>
<p>&nbsp; &nbsp;&nbsp;Search for businesses which support food delivery transactions.</p>
<ul>
    <li>
        <p>Business Details&nbsp;</p>
    </li>
</ul>
<p>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Get rich business data, such as name, address, phone number, photos, Yelp rating, &nbsp; &nbsp; &nbsp;price levels and hours of operation.</p>
<ul>
    <li>
        <p>Business Match&nbsp;</p>
    </li>
</ul>
<p>Find the Yelp business that matches an exact input location. Use this to match business data from other sources with Yelp businesses.</p>
<ul>
    <li>
        <p>Reviews</p>
    </li>
</ul>
<p>Get up to three review excerpts for a business.</p>
<ul>
    <li>
        <p>Auto complete&nbsp;</p>
    </li>
</ul>
<p>Provide autocomplete suggestions for businesses, search keywords and categories.</p>

<p>Now in our case we are using two endpoints.&nbsp;</p>
<ul>
    <li>
        <p><code>Business Search </code>(to get all the business and and get the business ids)</p>
    </li>
    <li>
        <p><code> Business Details </code> ( to get the business rich details )</p>
    </li>
</ul>
<p>First we are using a <code>business search endpoint </code>to get businesses from all of the states and categories and then we are storing the IDS of the business. To get business details we must need a business id. After storing the ids we are using a business Detail endpoint to get the details.&nbsp;</p>
<p>Now let&apos;s take a closer look at what kind of data we are receiving from each end point.&nbsp;</p>
<h3>1) &nbsp;Business Search Endpoint</h3>
  
<p>We can get business using search endpoints, for that we provide different parameters like <code>state, city, category, longitude, latitude, radius </code>.</p>
<p>We are providing <code>category</code>and <code>state names</code>to get all the results from each state with all categories.&nbsp;</p>
<p>Now we get some details from the search point as well but there is some other information that we need for our requirements. Information like Business hours, and price is provided in Business Detail Search Endpoint.&nbsp;</p>
<p>We are mainly using a business search endpoint to store <code>business ids</code> and then we are passing business ids to business details endpoint to get business details about individual business.&nbsp;</p>

<h3>2)Business Detail Endpoint:</h3>

<p>&nbsp;Business detail endpoint is used to get rich data about business with all the details.&nbsp;</p>
<p>We only need to provide a business id in order to get business details. In our case, as we were providing a list of all the business ids to get the business details in just one module.</p>
<h4>Business Details Schema:</h4>
<p><code>Business detail endpoint</code> provides many details about business like <code>Name, Address like City, state, zip code, and review count, overall_rating, price, hours, categories, longitude, latitude</code>and so on.</p>
<p>Here you can see the all schema or response body from the<a href="https://www.yelp.com/developers/documentation/v3/business">&nbsp;business search endpoint</a>.</p>
<p>We are only extracting some specific data and here is the list.&nbsp;</p>
<ul>
    <li>
        <p>Id</p>
    </li>
    <li>
        <p>Name</p>
    </li>
    <li>
        <p>Address</p>
    </li>
    <li>
        <p>State</p>
    </li>
    <li>
        <p>City</p>
    </li>
    <li>
        <p>Overall rating</p>
    </li>
    <li>
        <p>Review count</p>
    </li>
    <li>
        <p>Weekely_hours</p>
    </li>
    <li>
        <p>Price</p>
    </li>
    <li>
        <p>Category&nbsp;</p>
    </li>
</ul>
<h2>Yelp API Limitation&nbsp;</h2>
<p>Yelp API allows 50000 calls per day for one api. To get the api please refer to this page to get <a href="https://www.yelp.com/developers/v3/manage_app">yelp api</a>.&nbsp;</p>
<p>In our case we are using two endpoints so we can extract upto <code>~2K to 3K </code> business details per day. We are using <code>1122</code> api calls for getting business ids and then with every call we are getting at least 3 business. This results in <code>3450</code> business ids and then we are utilizing 3450 api calls to get business details.&nbsp;</p>
<p>So we get a max of <code>3450</code>of business per day.&nbsp;</p>
<p>If we want to get unique business everyday we just need to pass offset parameters as 3,6,9 and so on..</p>
<h3> Installation Guide </h3>
<code>pip install yelp_Data_process</code>

<h3> Code Exapmle </h3>
<h4> import libraries </h4>
<p> <code> import pandas as pd </code></p>
<p> <code> import numpy as np  </code></p>
<p> <code> from yelp_data_process import yelp_data_process  </code></p>

<h4> get api key </h4>
<p> <code> api_key = ''  </code></p>

<h4> get yelp dataset  </h4>
<p> <code> df = yelp_data_process.get_data(api_key) </code></p>

