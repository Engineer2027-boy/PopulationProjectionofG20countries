Population Projection of G20 Countries
______________________________________
A webapp created using flask and HTML that projects the population of G20 countries from 1950 to 2050.The population for year 2025-2050 is caclulated by using linear algebra(Least square method).  

Features 
________
The ability to choose the country whose projection you wish to be displayed.  
•The ability to choose upto which time period you wish to see.  
•A colorful graph that shows the population of the respective country you choose for the time period you choose.  
•A methdology document from which you can understand the methodology used to predict populations is available for download.  
•The data used for projections in .xlsx format is available for download.  
•Deployed using railway.app

Project Structure
_________________
├── static/ # Static files (images, documents)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── images/ App Screenshots  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──  docs/                  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── methodology.pdf  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└──demographics_of_g20_countries.xlsx           
├── templates/         #HTML files  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── homepage.html  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── population_projection.html  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; └── methodology.html  
├── requirements.txt # Python dependencies  
├── runtime.txt # Runtime version  
├── webapp.py # Main Flask application  
├── README.md # (this file)  



Author 
______
Ayush Aditya




