---
title: API Reference


toc_footers:
  - <a href='https://dashboard.vamonde.com/request-access/?direct=true' target="_blank">Sign Up for a Developer Key</a>
  - <a target="_blank" href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

Firstly, welcome and thank you for checking out the Vamonde API docs! Our API is designed to allow users to supplement their existing site with experiential content/stories, which can be filtered based on various use cases.

Please consult our <a href="https://solutions.vamonde.com" target="_blank">Introduction Page</a> for a broad overview of what we offer and our <a href="https://www.vamonde.com" target="_blank">Terms and Conditions</a> prior to using our API.

# Authentication

To make calls against the API the user will need to be authenticated. This is done by passing an Authorization header as shown below. If you do not have an API key, you will need to register for one at our <a href="https://dashboard.vamonde.com" target="_blank">dashboard</a>.

`Authorization: Token 1234567890abcdef`

<aside class="notice">
You must replace <code>1234567890abcdef</code> with your personal API key.
</aside>

# Experiences

You can think of experiences in Vamonde like an itinerary. Each experience is a group of `posts` (places) which work together to form a cohesive adventure for end users.

## Main Experience Fields

Below are the fields you are most likely going to use.

Field | Type | Description
--------- | -------- | -----------
profile_image_url | String | Main header and display image
description | String | Main overview for the experience
name | String | Display title
contributor | Object | Details about the publisher including a name and image
posts | Array | List of related posts (detail endpoint only)
translations | Array | List of IDs for translated versions of a given experience


## Get All Experiences

```json
{
    "count": 1215,
    "next": "https://api.vamonde.com/api/v1/adventures?page=2",
    "previous": null,
    "results": [
        {
            "banner_image_url": "",
            "banner_summary": "",
            "category": 14,
            "city_id": 3,
            "contributor": {
                "id": 585,
                "name": "Natalia Tellez",
                "profile_image_url": "https://s3.amazonaws.com/vamonde.media/provider/icon_vamonde.jpg",
                "created_at": "2019-08-15T14:25:23.677730Z",
                "updated_at": "2019-08-15T14:25:23.688163Z"
            },
            "created_at": "2020-02-06T18:20:11.267962Z",
            "default_bookmark": false,
            "description": "San Antonio is a tourist destination with several attractions, especially its amazing parks and gardens! Check out this list and be ready for an outdoors experience!\n\nPicture by CameliaTWU on Flickr. Attribution-NonCommercial-NoDerivs 2.0 Generic (CC BY-NC-ND 2.0)",
            "meta_description": null,
            "id": 1463,
            "is_active": true,
            "language": "en",
            "name": "Parks and Gardens San Antonio",
            "parent_adventure_id": null,
            "popularity": 0,
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2020-02-06T17%3A32%3A03.314Z.jpg",
            "protocol": [],
            "summary": "",
            "deep_link": "https://vamonde.app.link/bLSSMFhDR3",
            "tags": [
                "Natalia Tellez"
            ],
            "translations": [],
            "updated_at": "2020-02-06T18:20:11.599805Z",
            "contributors": [
                585,
                1
            ]
        },
    ]
}
```

Returns a list of experiences which is filterable as shown below. Does not include any content from the related posts.

### HTTP Request

`GET https://api.vamonde.com/api/v1/adventures`

### Query Parameters

Parameter | Description
--------- | -----------
category_group | Filters content based on a grouping of categories
category_id | Filters content based on a single category
city_id | Filters content to a given city
search | Filters content by matching search term to titles, descriptions, and tags

### Optional Parameters (hotels)

These parameters will alter the content returned based on our personalization algorithm. This set is catered to hotel data, but can be utilized in a number of other circumstances.

These parameters should **not** be used in conjunction with the `category_group`, `category_id`, or `search` parameters.

Parameter | Description
--------- | -----------
number_of_guests | Number of guests for a given reservation
trip_duration | Amount of time, in days, a person booked a reservation for
has_child | Fetches age-appropriate and family driven content based on if children are present or not
lat/lng | Fetches content nearby a given location, usually your destination. Must include both parameters.

## Experience Details

```json
{
    "banner_image_url": "",
    "banner_summary": "",
    "category": 15,
    "city_id": 1,
    "contributor": {
        "id": 271,
        "name": "Chicago Scene",
        "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F271%2FContributor_271_2018-07-06T21%3A03%3A47.949Z.jpg",
        "created_at": "2018-06-22T16:37:50.553606Z",
        "updated_at": "2019-09-21T21:26:09.256029Z"
    },
    "created_at": "2018-12-27T23:48:56.268951Z",
    "default_bookmark": false,
    "description": "It's where the infamous Al Capone use to party like a rockstar with a dash of scandal. During the Prohibition Era, beneath the streets and \"all that jazz\", illicit activities were occurring. And, hidden escape routes to elude the Chicago police existed in the Underground Tunnels.",
    "meta_description": "",
    "id": 532,
    "is_active": true,
    "language": "en",
    "name": "Uptown",
    "parent_adventure_id": null,
    "popularity": 48,
    "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2018-11-30T20%3A59%3A11.441Z.jpg",
    "protocol": [],
    "summary": "",
    "deep_link": "https://vamonde.app.link/doWenlN9ZS",
    "tags": [
        "Chicago Scene",
        "Al Capone",
    ],
    "translations": [],
    "updated_at": "2020-02-03T21:22:34.651727Z",
    "contributors": [
        271,
        1
    ],
    "posts": [
        {
            "id": 3347,
            "adventure": 532,
            "contributor_id": "271",
            "categories": [
                15
            ],
            "address": "1333 W Argyle St, Chicago, IL 60640, USA",
            "name": "Essanay Studios",
            "description": "Take a step back in time with this iconic silent film studio, the creative home of Charlie Chaplin.",
            "meta_description": "",
            "location": {
                "latitude": "41.97235939999999",
                "longitude": "-87.6627919"
            },
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FPost_1_2018-12-20T23%3A06%3A52.462Z.jpg",
            "items": [...], // post content
            "protocol": [],
            "tags": [],
            "place_id": "",
            "created_at": "2018-12-27T23:48:56.561099Z",
            "updated_at": "2020-02-03T21:22:54.768890Z",
            "total_likes": 0,
            "is_liked": false,
            "city": 1
        }
    ]
}
```

Returns details about a specific experience including information about it's related `posts`.



### HTTP Request

`GET https://api.vamonde.com/api/v1/adventures/<ID>`

# Posts

Where Experiences are like an itinerary, a Post is a detailed story about each destination. Every post has a physical location, and every post will be part of an Experience.

## Main Post Fields
Below are the fields you are most likely to be using.

Field | Type | Description
--------- | -------- | -----------
profile_image_url | String | Main header and display image
name | String | Display title
description | String | Main overview of the post
items.Body | Array | Array of different types of post content, detailed below


## Post Content Fields

```json
[
    // Paragraph
    {
        "Key": "text_b3382530-49de-11ea-9fbb-3532d6fd81e5",
        "Link": "none",
        "Text": "Standard paragraph module",
        "Type": "Label",
        "Property": "Text",
        "SourceName": "none"
    },

    // Header
    {
        "Key": "header_bc470600-49de-11ea-9fbb-3532d6fd81e5",
        "Link": "none",
        "Text": "header / content separation",
        "Type": "Label",
        "Property": "H1",
        "SourceName": "none"
    },

    // Quote
    {
        "Key": "quote_ce2e7560-49de-11ea-9fbb-3532d6fd81e5",
        "Link": "none",
        "Text": "quoted content or reiteration",
        "Type": "Label",
        "Property": "Quote",
        "SourceName": "none"
    },

    // Image Gallery
    {
        "Key": "images_e2a939d0-49de-11ea-9fbb-3532d6fd81e5",
        "Type": "Gallery",
        "Images":
        [
            {
                "Key": "e55239c0-49de-11ea-9fbb-3532d6fd81e5",
                "Link": "",
                "Text": "describing our image, useful for meta as well",
                "SourceName": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2020-02-07T19%3A20%3A26.797Z.png"
            }
        ],
        "Property": "Vertical"
    },

    // Youtube video
    {
        "Key": "video_09c15020-49df-11ea-9fbb-3532d6fd81e5",
        "Link": "none",
        "Text": "",
        "Type": "Video",
        "Property": "Single",
        "SourceName": "fc51YqV5nSw"
    },

    // CTA
    {
        "Key": "quote_268457c0-4773-11ea-8620-67ae960ae29d",
        "Link": "http://google.com",
        "Text": "Check out this event",
        "Type": "Html",
        "Image": "https://s3.amazonaws.com/vamonde.media/adventures%2Faf58ce13-3fed-403c-85b4-2c4aac33c07f%2FWidget_af58ce13-3fed-403c-85b4-2c4aac33c07f_2020-02-04T17%3A24%3A14.871Z.png",
        "Button": "LINK TEXT",
        "Property": "Quote",
        "SourceName": "",
        "ImageDimensions":
        {
            "width": 137.0307167235495,
            "height": 100
        }
    },

    // Divider
    {
        "Key": "divider_12bca8f0-49df-11ea-9fbb-3532d6fd81e5",
        "Link": "none",
        "Text": "none",
        "Type": "Divider",
        "Property": "none",
        "SourceName": "none"
    },

    // Event
    {
        "Key": "eventwrapper_14e35980-49df-11ea-9fbb-3532d6fd81e5",
        "Type": "Event",
        "Event": {...}
    }
]
```

Each item inside the `Post.items.Body` field contains a set of information about how each should be displayed. These are based primarily on the `Type` and `Property` fields within.

Item Type | Properties | Description of Type
--------- | -------- | ---------
Paragraph | `{Property: "Text", Type: "Label", Text: "content here"}` | Main content type, basic paragraph with no special styling
Header | `{Property: "H1", Type: "Label", Text: "content here"}` | Basic header used for introductions and separating sections
Quote | `{Property: "Quote", Type: "Label", Text: "content here"}` | Quoted content from a speaker or external source, or used to reiterate content. Should be visibly distinct and typically displayed with stylistic elements
Image Gallery | `{Type: "Gallery", Images: [{ SourceName: "url.jpg", Text: "caption text" }]}` | A group of images and their captions. Should be displayed together in a grid or slider type of display along with provided captions
Youtube Video | `{Type: "Video", SourceName: "youtubeVideoID"}` | Provides the ID of a youtube video which can be used to fetch and play the video
Call to Action | `{Type: "Html", Image: "imageSrc.png", Text: "Headline text" Button: "Button Text", Link: "buttonDestination.com"}` | A call to action widget that consists of an image, tagline, and a link with text. Typically used for event details or ticketing off platform
Divider | `{Type: "Divider"}` | A horizontal visual seperation in content
Event | `{Type: "Event", Event: { ...eventData }}` | For linking an event published on Vamonde, includes all data found without our Event model

## Get All Posts

```json
{
    "count": 7539,
    "next": "https://api.vamonde.com/api/v1/posts?category_group=2&page=2",
    "previous": null,
    "results":
    [
        {
            "id": 7749,
            "adventure": 1294,
            "address": "Elliot Park, Minneapolis, MN, USA",
            "name": "Elliot Park",
            "description": "This rapidly gentrifying area is popular with young professionals",
            "location":
            {
                "latitude": "44.969848",
                "longitude": "-93.2627316"
            },
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FPost_1_2019-09-17T19%3A20%3A17.592Z.jpg",
            "items":
            [
                {
                    "Body": [...],
                }
            ],
            "protocol": [],
            "summary": "",
            "created_at": "2019-10-09T16:28:11.956987Z",
            "updated_at": "2019-10-24T21:22:57.718907Z",
            "parent_post_id": null,
            "contributor_id": null,
            "categories":
            [
                15
            ],
            "city": 31,
            "total_likes": 0,
            "place_id": "",
            "tag_array": [],
            "post_rating":
            {
                "text": 3,
                "media": 1,
                "headers": 3,
                "first_item_header": true,
                "total": 7
            },
            "popularity": 0
        },
    ],
    ...
}
```

Returns a list of posts which is filterable as shown below. Does not include the post's content

### HTTP Request

`GET https://api.vamonde.com/api/v1/posts`

### Query Parameters

Parameter | Description
--------- | -----------
category_group | Filters content based on a grouping of categories
category_id | Filters content based on a single category
city_id | Filters content to a given city
search | Filters content by matching search term to titles, descriptions, and tags
lat/lng | Fetches content nearby a given location, usually your destination. Must include both parameters.

### Optional Parameters (hotels)

These parameters will alter the content returned based on our personalization algorithm. This set is catered to hotel data, but can be utilized in a number of other circumstances.

These parameters should **not** be used in conjunction with the `category_group`, `category_id`, or `search` parameters.

Parameter | Description
--------- | -----------
number_of_guests | Number of guests for a given reservation
trip_duration | Amount of time, in days, a person booked a reservation for
has_child | Fetches age-appropriate and family driven content based on if children are present or not

## Post Details

```json
{
    "id": 5233,
    "adventure": 671,
    "address": "440 S Main Ave, Tucson, AZ 85701, USA",
    "name": "D: Carrillo Elementary School",
    "description": "This lovely school building was named after Leopoldo Carrillo, the developer of Carrillo Gardens.",
    "location":
    {
        "latitude": "32.2152945",
        "longitude": "-110.97474019999999"
    },
    "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FPost_1_2019-08-13T23%3A21%3A22.182Z.jpg",
    "items":
    [
        {
            "Body": [...], // Post Content
        }
    ],
    "protocol": [],
    "summary": "25",
    "created_at": "2019-08-06T17:56:07.091015Z",
    "updated_at": "2020-02-03T21:22:57.077508Z",
    "parent_post_id": null,
    "contributor_id": 545,
    "categories":
    [
        15
    ],
    "city": 10,
    "total_likes": 0,
    "place_id": "",
    "tag_array": [],
    "post_rating":
    {
        "text": 1,
        "media": 1,
        "headers": 1,
        "first_item_header": false,
        "total": 3
    },
    "popularity": 32
}
```

Returns content and details for a specific post

# Events

Events on Vamonde work like events on many other platforms. While we don't offer ticketing at this time, we provide direct links to detail or checkout pages which are differentiated.

<aside class="notice">
We periodically clean our events and remove expired events. Due to this, we recommend not saving event data or IDs as there is no guarantee they will be active next time they are referenced.
</aside>

## Main Event Fields

Below are the fields you are most likely to be using.

Field | Type | Description
--------- | -------- | -----------
banner_image_url | String | Main header and display image
img_urls | Array | List of supplementary images
title | String | Name of the event
description | String | Main overview of the event
location | Object | Contains a `latitude` and `longitude` property for the location of the event
start_time, end_time | Date | Time, in UTC, when an event is taking place
web_link | String | Event detail page, usually straight from the source. Most likely does not have a direct link to buy at ticket
buy_link | String | Direct link to purchase a ticket, if provided
price_min, price_max | String | Representation of the maximum and minimum prices found for tickets for a given event

## Get All Events

```json
{
    "count": 20,
    "next": null,
    "previous": null,
    "results":
    [
        {
            "id": 285081,
            "title": "Toys Ahoy! A Maritime Childhood",
            "description": "Adventure is out there! Toys Ahoy! is a new and fun exhibition that connects the young and the young at heart.\n\nWith almost 100 different items on display such as children’s books, games and toys, this exhibit will excite everyone of all ages! The collection includes wood and paper battleships, board games, card games, puzzles, motorized miniature engines and other historic toys and collectibles from years gone by. Free with $1 admission.",
            "start_time": "2019-12-04T14:00:00.000000Z",
            "end_time": "2020-09-07T21:00:00.000000Z",
            "banner_img_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2019-12-04T17%3A14%3A56.973Z.jpg",
            "img_urls":
            [
                "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2019-12-04T17%3A15%3A08.924Z.jpg",
                "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2019-12-04T17%3A15%3A28.487Z.jpg"
            ],
            "buy_link": null,
            "web_link": "https://www.marinersmuseum.org/",
            "venue": null,
            "address": "100 Museum Dr, Newport News, VA 23606, USA",
            "city": "Newport News",
            "state": "VA",
            "country": "US",
            "zip": "23606",
            "location":
            {
                "latitude": "37.0551904",
                "longitude": "-76.48808409999998"
            },
            "phone_number": "(757) 596-2222",
            "channel": null,
            "category": 10,
            "contributor": 667,
            "priority": 20,
            "price_min": "1.00",
            "price_max": "1.00",
            "source_id": null,
            "source": null
        },
       ...
    ]
}
```
Returns a list of events which is filterable as shown below.

### HTTP Request
`GET https://api.vamonde.com/api/v1/events`

### Query Parameters

Parameter | Description
--------- | -----------
category_group | Filters content based on a grouping of categories
category_id | Filters content based on a single category
city | Filters based on a city name EX. "chicago"
search | Filters content by matching search term to titles, descriptions, and tags
lat/lng | Fetches content nearby a given location, usually your destination. Must include both parameters.
start_date | Fetches events happening on or after a specific date
end_date | Limits events returned to before a specific date

### Optional Parameters (hotels)

These parameters will alter the content returned based on our personalization algorithm. This set is catered to hotel data, but can be utilized in a number of other circumstances.

These parameters should **not** be used in conjunction with the `category_group`, `category_id`, or `search` parameters.

Parameter | Description
--------- | -----------
number_of_guests | Number of guests for a given reservation
trip_duration | Amount of time, in days, a person booked a reservation for
has_child | Fetches age-appropriate and family driven content based on if children are present or not

## Event Details

```json
{
    "id": 285081,
    "title": "Toys Ahoy! A Maritime Childhood",
    "description": "Adventure is out there! Toys Ahoy! is a new and fun exhibition that connects the young and the young at heart.\n\nWith almost 100 different items on display such as children’s books, games and toys, this exhibit will excite everyone of all ages! The collection includes wood and paper battleships, board games, card games, puzzles, motorized miniature engines and other historic toys and collectibles from years gone by. Free with $1 admission.",
    "start_time": "2019-12-04T14:00:00.000000Z",
    "end_time": "2020-09-07T21:00:00.000000Z",
    "banner_img_url": "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2019-12-04T17%3A14%3A56.973Z.jpg",
    "img_urls":
    [
        "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2019-12-04T17%3A15%3A08.924Z.jpg",
        "https://s3.amazonaws.com/vamonde.media/adventures%2F1%2FDraftAdventure_1_2019-12-04T17%3A15%3A28.487Z.jpg"
    ],
    "buy_link": null,
    "web_link": "https://www.marinersmuseum.org/",
    "venue": null,
    "address": "100 Museum Dr, Newport News, VA 23606, USA",
    "city": "Newport News",
    "state": "VA",
    "country": "US",
    "zip": "23606",
    "location":
    {
        "latitude": "37.0551904",
        "longitude": "-76.48808409999998"
    },
    "phone_number": "(757) 596-2222",
    "channel": null,
    "category": 10,
    "contributor": 667,
    "priority": 20,
    "price_min": "1.00",
    "price_max": "1.00",
    "source_id": null,
    "source": null
}
```

Get details for a specific event

### HTTP Request
`GET https://api.vamonde.com/api/v1/events/<ID>`

# Categories + Category Groups

Our endpoints typically expect you to send either a category ID or category group ID to filter by them. Category groups contain a priority-based ordering of categories, using a category group filter will attempt to use the priority to skew results towards those categories.

Both categories and category groups can be fetched for filtering options or prior to other requests to use as filters.

## Get all categories

```json
{
    "count": 12,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 3,
            "name": "Architecture",
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures/Category:IWhdEsbjAd:image",
            "color": "#8C8FAE",
            "is_active": true
        },
        {
            "id": 6,
            "name": "Art & Theatre",
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/adventures/Category:8jELKHrJiJ:image",
            "color": "#70377F",
            "is_active": true
        },
        ...
    ]
}
```

### HTTP Request

`GET https://api.vamonde.com/api/v1/categories`

### Category Fields

Field | Description
--------- | -----------
color | Unique color code for each category
profile_image_url | Default image for each category

## Get all category groups

```json
{
    "count": 5,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 1,
            "name": "Tourist",
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/categories/image_tourist.jpg",
            "icon_url": "https://s3.amazonaws.com/vamonde.media/categories/cat_Tourist.png",
            "categories": [
                1,
                17,
                3,
                6,
                7,
                12,
                15
            ],
            "is_active": true
        },
        {
            "id": 2,
            "name": "Local",
            "profile_image_url": "https://s3.amazonaws.com/vamonde.media/categories/image_local.jpg",
            "icon_url": "https://s3.amazonaws.com/vamonde.media/categories/cat_Local.png",
            "categories": [
                17,
                2,
                4,
                7,
                12,
                15
            ],
            "is_active": true
        },
        ...
    ]
}
```

### HTTP request

`GET https://api.vamonde.com/api/v1/category-groups`

### Category Group Fields

Field | Description
--------- | -----------
profile_image_url | Default image for each category group
icon_image_url | More stylistic icons for each category group
categories | List of categories for each category group