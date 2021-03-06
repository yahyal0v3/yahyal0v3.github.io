---
layout: post
title:      "CLI Data Gem Project"
date:       2017-11-16 20:45:38 -0500
permalink:  cli_data_gem_project
---


For my project I created a gem for viewing the top 20 best selling books of the year according to Amazon's and Barnes & Noble's website. The first prompt asks the user whether they would like to see Amazon's or Barnes & Noble's best sellers. When given valid input the program then displays the top 20 list from the selected site. Aside from other options such as exiting or returning to the list, the second prompt that appears asks the user to select a listing if they would like to view additional details about the book. If the user selects a listing, the program displays a list of additional information options, such as 'Author Bio', 'Price', 'Available format', 'Site rating', and 'Link'. The last main prompt asks the user to select which one they would like to view. 

Before starting my code, I jotted down how I wanted my program to flow and how it would work. I think what was most important was figuring out which classes would be responsible for what. The CLI class would be responsible for giving the user prompts and displaying the best sellers lists and the details of each book. The site classes would be responsible for scraping the book lists and book details, and would have many books--because when the user selected a site, that site's best selling books would be displayed. There would also need to be a books class to create book instances and assign characteristics. The data from the site's scraper method would be used to assign those characteristics. 

[30 Min Coding Session](https://soapbox.wistia.com/videos/TkTttQWuc0)

Because I was scraping from two different sites, I knew that I needed to have two seperate classes--an Amazon class and a Barnes & Noble class, because they would have to use different links and scrape information in different ways. And somehow these two classes had to be connected to something greater, something they would have to inherit from. At the very beginning I was imagining them as children, but then I realized it wouldn't be a parent Site class I'd need. I wouldn't need the parent class to initialize anything, it was just an umbrella of methods my Amazon and B&N classes needed. In the program, when the user typed in the site they wanted to view the list of, there would also need to be a way to let the method know which list they had to print out. A module was the answer. With a module, I would be able to avoiding rewriting the same code and be able to tell the program to run Amazon.list_best_sellers or BarnesNNoble.list_best_sellers just by adding the class name depending on the site the user chose.

Writing the actual program, I started with the CLI class's call method and worked backwards. I was a little surprised at how natural a process it was. When running into an error and having to figuring out what to do next, instead of it being ambigious, like looking at an empty area in a puzzle set, the missing pieces that had to come next had an obvious shape and identity that I just had to fill out. When just focusing on writing the code first and not paying attention to giving methods one specific purpose, I found that some methods also naturally seperated. For example, having to seperate code and make it it's own individual method in the CLI class so that it can call itself and loop back if the user gives invalid input.


One of the things I had dwelled a lot on throughout the process was whether my site classes where metaphorically correct. The site classes had their own book lists, and they also scraped data from their actual website. Something seemed off about this, especially since in previous lessons the scraper was it's own class. But was I to really write two different scrapers, AmazonScraper and BarnesNNobleScraper, and then two site classes? It might technically be more organized, but it seemed so unnecessary. Then I  realized, like modules, classes could be nested--which I thought would be a great was to seperate but still keep the site classes' methods together.    

Working backwords, one of the final things I had to do was actually scrape data from the two sites instead of having placement filler. Summarizing the process of the actual program, the scraper methods iterate through the website's best sellers list and stores each book's data in a hash. The collectable module, shared by both the Amazon and Barnes & Noble class, then uses the scraped hash to create book instances, store them in the class's .all_books method, and then lists the best sellers using .all_books.  

[Gem published to RubyGems](https://rubygems.org/gems/best_selling_books)

