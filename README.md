# Dime Pub
Simple web RSS reader implemented with "ASP.NET Core Web App". 
It aggregates **RSS feeds as podcast channels** and populates **recent RSS items as episodes**.

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <!-- <li><a href="#contributing">Contributing</a></li> -->
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <!-- <li><a href="#acknowledgments">Acknowledgments</a></li> -->
  </ol>
</details>

## About The Project

[![Screenshot](https://raw.githubusercontent.com/jackie4u/dime-pub/main/Screenshot-Index-01.jpg)](https://dimepub.azurewebsites.com)

This project is only intended as a study project on which I tried to develop **my first web app**.

Web app aggregates RSS feeds for **podcast channel** and populates recent **episodes (RSS items/articles)**.

It is implemented as a simple RSS reader in ASP.NET Core (Mode-View-Controller) with .Net 6.0 and Entity Framework Core 6.
For GUI is used Bootstrap 5 and some icons from Font Awesome 6.

I have tried to separate the data layer into a stand-alone project **FeedDataLibrary** with repository pattern and MVVM approach.
But I have not grasped these concepts appropriately yet, so it needs further refactoring.

There are currently some bugs and not implemented features. Some of them are marked in a comment with *TODO* tag .

### Built With

* ASP.NET Core Web App (Mode-View-Controller)
* .Net 6.0 (LTS)
* Entity Framework Core 6
* Microsoft SQL Server
* Bootstrap 5
* Font Awesome 6

## Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

* Install .NET 6 (SDK and Runtime) from https://dotnet.microsoft.com/en-us/download/dotnet/6.0
* Install powershell global tools
  ```powershell
  dotnet tool install dotnet-ef -g
  dotnet tool install Microsoft.Web.LibraryManager.Cli -g
  ```
* Install Microsoft SQL Server from https://www.microsoft.com/en-in/sql-server/sql-server-downloads

### Installation

1. Clone the repo
```sh
   git clone https://github.com/jackie4u/dime-pub.git
```

2. Enter the name of your SQL Server in `appsettings.json` and eventually change the database name and security
```json
  {
    "Logging": {
      "LogLevel": {
        "Default": "Information",
        "Microsoft.AspNetCore": "Warning"
      }
    },
    "AllowedHosts": "*",
    "ConnectionStrings": {
      "DimePubConnection": "Data Source=<SQL Server>; Initial Catalog=DimePubDb; Integrated Security=True"
    }
  }
```

3. Initialize database
```powershell
   cd FeedDataLibrary/dime-pub
   dotnet ef --startup-project ../DimePubWeb database update
```

4. Run the application
```powershell
   dotnet run
```

## Usage

The content of the web app focuses on aggregating podcast RSS feeds.

### Episodes (articles):
- The index page lists all episodes (articles)
- If you are on a different page click on "Episodes" link in the top menu
- By default, there are shown only the latest 10 episodes - for older episodes follows page numbers at the bottom of the page
- To filter episodes (articles) by date choose the date range from the top header and press "Filter"
- To Reload all episodes (articles) from all podcasts (feeds) press the button "Refresh all"

### Podcasts (feeds):
- To list all podcasts (feeds) click on "Podcasts" link in the top menu
- To filter podcasts (feeds) by title enter string into the search textbox and press "Search"
- To check the detail of the selected podcast (feed) and list all episodes (articles) in that podcast click on the "Detail" link in the "Podcasts" table
- To delete a podcast (feed) click on the "Delete" link in the "Podcasts" table or the "Delete" button on the podcast detail page
- To Reload articles in selected podcast (feed) press button "Refresh" on the podcast detail page

#### To add a new RSS feed 
1. **click on "Add new podcast"** 
2. enter the "Source URL" of your favourite podcast channel - for example, Coding Blocks at "https://www.codingblocks.net/podcast-feed.xml"
3. optionally add your custom "Podcast Note"
3. press the button "Save new podcast feed"

## Roadmap

- [ ] Implement about page
- [ ] Improve graphic design
- [ ] Add checkboxes for deleting multiple podcasts from the podcast list
    - [ ] Add button for checking all checkboxes
- [ ] Implement error handling
- [ ] Add sorting to list views and tables
    - [ ] Add sorting to podcasts
    - [ ] Add sorting to episodes
- [ ] Implement IsRead flag

See the [open issues](https://github.com/jackie4u/dime-pub/issues) for a full list of proposed features (and known issues).

## Contributing

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. 
See `LICENSE.txt` for more information.

## Contact

Twitter - [@jackie4u](https://twitter.com/jackie4u)

## Acknowledgments

**This project is influenced by learning from the great book ["Pro ASP.NET Core 6: Develop Cloud-Ready Web Applications Using MVC, Blazor, and Razor Pages"](https://www.amazon.com/dp/B09TDKPSCZ) by [Adam Feeman(MarkP88)](https://github.com/MarkP88).**

[contributors-shield]: https://img.shields.io/github/contributors/jackie4u/dime-pub.svg?style=for-the-badge
[contributors-url]: https://github.com/jackie4u/dime-pub/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/jackie4u/dime-pub.svg?style=for-the-badge
[forks-url]: https://github.com/jackie4u/dime-pub/network/members
[stars-shield]: https://img.shields.io/github/stars/jackie4u/dime-pub.svg?style=for-the-badge
[stars-url]: https://github.com/jackie4u/dime-pub/stargazers
[issues-shield]: https://img.shields.io/github/issues/jackie4u/dime-pub.svg?style=for-the-badge
[issues-url]: https://github.com/jackie4u/dime-pub/issues
[license-shield]: https://img.shields.io/github/license/jackie4u/dime-pub.svg?style=for-the-badge
[license-url]: https://github.com/jackie4u/dime-pub/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/vackar
[product-screenshot]: images/screenshot.png
