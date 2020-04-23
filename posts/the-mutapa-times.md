---
title: "The Mutapa Times "
date: 2020-04-23T15:54:47.533Z
summary: "I made something for Zimababwe :) "
tags:
  - post
---
## What?

![](/static/img/newspaper_auschnit02.gif)

The Mutapa Times is an online newspaper that aggregates Zimbabwean news from foreign press in 3 categories from over 100 different sources to deliver a curated platform for diverse Zimbabwean news.

## Why?

![](/static/img/perpetual-motion-machine-gif-fix.gif)

In a recent interview veteran journalist Everjoice Win, said that "the media is failing the people of Zimbabwe by not giving accurate information or emulating how some foreign media are reporting COVID-19 - with empathy and compassion, while still protecting human rights.

For this reason the paper aims to inform people regarding matters within Zimbabwe using a diverse range of perspectives.

## Who?

![](/static/img/2ai8u0.gif)

The newspaper is for the diaspora & native residents of the nation with the most joyous people on earth, Zimbabwe.

## How?

```javascript
    function getData() {
      $.ajax({
        type: "GET",
        url: apiUrl + test1+"&to="+z+"&"+"apiKey=" + apiKey,
        datatype: "jsonp",
        success: function(data) {
          newsArr.push(data);
          insertData();
        }
      });
    }
  
    function insertData() {
      $(".date").append(date.toLocaleDateString("en-US", options));
      $(".vol").append("Issue # " + volNum + " | Page 4");
      for (let i = 1; i < newsArr[0].articles.length; i++) {
        index = i - 1;
        let news = newsArr[0].articles[index];
        if (news.description && news.source.id != "zim-news") {
          if (count < 4 && news.urlToImage) {
            $(".image" + count).attr("src", news.urlToImage);
            printData(news);
          } else if (count >= 4) {
            printData(news);
          }
          if (count === 8) {
            return true;
          }
        }
      }
    }
  
    function printData(news) {
      $(".storyTitle" + count).append(news.title);
      $(".story" + count).append(news.description);
      $(".by" + count).append("Source: " + news.source.name);
      $(".a" + count).attr("href", news.url);
      count++;
    }
```

The Mutapa Times was built by @eluwasi using the News API. News API is a simple HTTP REST API for searching and retrieving live articles from all over the web with code.

The paper features the most popular news stories featuring "Zimbabwe" over the last 7 days. The paper searches the web every 15 minutes looking for new articles, should one of those become popular (a lot of clicks) it will end up on the paper.