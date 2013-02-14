Bootstrap-Themes-Summer-2012-Release 1.0
====================================

All new themes for the summer 2012 release

Summary:

We've moved to bootstrap for Django Market and Shops. This is the default theme for Django market and the associated support files to build from source

Structure:

The source cotains 3 directories and two files. 

Files:

Readme.md (what your're reading now)

License-Apache2.0txt License for all work developed by Stephen Power, others such as Bootswatch and Bootstra

Folders:

There are two themes, Default and Orange-News. Below is a summary and short documentation for the themes. 

Summary 

default.zip - This is the "compiled" zip file that contains all the necessary items for a django shop theme.

OrangeNews.zip - Same just for the Orange News Theme


less: Contains a customized variables.less and an included responsive.less. This readme is unable to explain the less "dynamic stylesheet language"
 
ScreenShots: So you don't have to install Django Market and the default shop, I give you a peek at what it looks like (at least on my imac 2009 running 10.8.2)

theme - This is the heart of the theme in these two folders. It contains two subdirectories:

Assets - Contain all the image, css, javascript and any other supporting files for a theme. 

Templates - Contain all the required templates for the theme. Please alter the template as you see fit for layout / use, but all must be there and provide the documented functionality to work. Please see Collector City Documentation for more information. 

To Use the Theme as is: Go to: Admin Site | Web Store Tab | Theme | On the Gear, click import and point to the zip file.

To modify: 

CSS: I suggest modifying the CSS using the less "the dynamic stylesheet language" 

Templates: In the beginning, you'll want to edit them in the shops to get an instant feedback on how they look, overtime you'll use your favorite text editor. 

Assets: Add them to folder. In the template, please refer to them using the ASSET_URL variable. 

Example:

<title>{{ shop_name }} - {{ page_title }}</title>
<meta name="description" content="{{ page_description }}"/>
<link rel="stylesheet" href="{{ 'screen.css' | asset_url }}"/>
<link rel="stylesheet" href="{{ 'buttons.css' | asset_url }}"/>
<link rel="stylesheet" href="{{ 'css.css' | asset_url }}" />

Quick and Dirty Documentation:

Layout.html
URL - none
Summary: Provides the "base" template that all other templates are "folded" into. Think of layout.html as the "parent" template that all "children" are folded into. Where does this take place? The {{ content }} variable is replaced by each of the children by URL

home.html
URL / and /home/
Summary: provide the homepage experience for the user. This is a key page, and great care should be taken care of on what goes on this page. 

Know Bugs: My Orders Template has a bug that has to wait until Sunday to fix. Its getting late.

Credits:
Bootstrap: Bootstrap is a sleek, intuitive, and powerful front-end framework for faster and easier web development, created and maintained by Mark Otto and Jacob Thornton at Twitter.

To get started, checkout http://getbootstrap.com!

Bootswatch: Spacelab Theme: https://github.com/thomaspark/bootswatch Copyright 2012 Thomas Park

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

## Local Designer Tool

Have you ever wanted to develop the templates on your local machine, and see what it looked like in production, well, thanks to the beauty of open source and contributors around the world, we have a simple tool for designers

Requirements: Python 2.x

Directions. 

Copy the file dm-design-local.py from the folder Local-Designer-Tool folder to the root folder. The folders assets and templates should be subfolders to the folder that dm-design-local.py is in.

This is important. You'll get crazy errors due to the assumption of folder structure. 

next run python dm-design-local.py

Two folders are created 

design
url-assets

design is the out put of the site layout, html, css and page template. Each template is combined with the layout.html to create a "stand alone" web page for local viewing. 

The {{ content }} variable in the layout is replaced by each of the page templates. This is a key concept.

The templating media URL use the following to resolve the static media url. To avoid changing the source. A fourth folder will be created: assets-url

Variable replacement:

Like all good templating engines, Django Market relies on variables that are calculated at render. For design purposes, we have made the following assumptions for layout.html and home.html

General Variables:

All media / static files must be copied to there and the url variables point to that for the {{ 'filename.extension' | asset_url }} variables. 

For this version, /assets-url/filename.extension

This will ensure the css, javascript etc are loaded to show how the site actually looks. without altering the source files.  

Example:
{{ 'css.css' | asset_url }} 

Other Variables for layout.html:

{{ shop_name }} = Django Market Theme Designer 
{{ page_title }}  = Django Market (html-name.html) Page
{{ url_search }} = search.html
{{ url_my_shopping }} = my_shopping.html
{{ total_cart_items }} = 10
{{ page_description }} = leave blank
{{ header }} = leave blank
{{ flash }} = leave blank

{{ menu }} = Replace with the following block of html
<ul id="menu-primary" class="menu">
		<li><a href="home.html">Home</a></li>
		<li><a href="for_sale.html">For Sale</a></li>
		<li><a href="auctions.html">Auctions</a></li>
		<li><a href="blog.html">Blog</a></li>
		<li><a href="about_us.html">About Us</a></li>
    	<li><a href="login.html" id="">Login</a></li>
		<li><a href="register.html">Register</a></li>
</ul>

{{ about|truncate(100) }} replace with 100 characters of ipsum 
{{ last_post.url }} = blog.html 
{{ last_post.title }} = Django Market Blog Post
{{ last_post.date_time }} = Today's Date

{% for link in links %}
<p><a href="{{ link.to }}">{{ link.name }}</a></p>
{% endfor %}
with
<p><a href="home.html">Home</a></p>
<p><a href="auctions.html">Auctions</a></p>
<p><a href="for_sale.html">For Sale</a></p>
<p><a href="login.html">Login</a></p>
<p><a href="register.html">Register</a></p>

home.html

Note: not all variables may be listed on each page.

{{ home.title }} = Django Market Home Page
{{ home.body }} Replace with 100 words of ipsum
{{ url_refund  }} = refund.html
{{ url_privacy_policy  }} = privacy_policies.html 
{{ url_terms_of_service  }} = terms_of_service.html 
{{ mailing_list }} with this block of html
<div id="mail_list_form">
<form action="." method="POST" name="form">
		<label for="id_email">Enter Your Email Address:</label>
		<input id="id_email" type="text" name="email" maxlength="75" />
		<input type="submit" class="btn btn-primary" value="Subscribe" id="mail_list_submit_btn"></input>
	</form>
</div>

{{ home.image.url }} =  http://s3.amazonaws.com/market-media.greatcoins.com/img/no-photo-shop.png

This will allows the home page to accuratly reflect the html, css, javascript and the layout. 

Future: the next version will allow variable replacement for the other pages in the layout. Currently, if you go to my_shopping.html the template variables are interpeted at HTML text. Its ugly, I know, but this is a simple way to see your site, with a good layout.

Feel free to change the variables as needed, those are just suggestions.


Other ideas: 

This will be our build tool to minify the js, css, tidy the html, css etc. also, it will help gzip the files. This is extremely important to our performance goals moving forward, combined with our integration to Amazon Cloud Front.


