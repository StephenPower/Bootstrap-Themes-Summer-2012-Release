Bootstrap-Themes-Summer-2012-Release 1.0
====================================

All new themes for the summer 2012 release

Summary:

We've moved to bootstrap for Django Market and Shops. This is the default theme for Django market and the associated support files to build from source

Structure:

The source cotains 3 directories and two files. 

Files:

Readme.md (what your're reading now)

theme.zip - This is the "compiled" zip file that contains all the necessary items for a django shop theme.

Folders:

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