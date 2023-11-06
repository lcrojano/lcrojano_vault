---
url: https://laravel-news.com/filter-api-responses-with-laravel-purity
readlater:
  id: "3957829076"
  provider: pocket
  synchtime: 1699293690038
---
# Filter API Responses with Laravel Purity

Last updated on October 31st, 2023 by [Paul Redmond](/@paulredmond)

The Laravel [Purity](https://github.com/abbasudo/laravel-purity) package is an elegant and efficient filtering and sorting package for Laravel, designed to simplify complex data filtering and sorting logic for [eloquent queries](https://laravel-news.com/writing-to-the-database-with-eloquent). By simply adding `filter()` to your Eloquent query, you can add the ability for frontend users to apply filters based on URL query string parameters like a breeze.

Let's say that your controller returns a collection of books, and you want to allow filtering by category slug `mystery`:

```
return Book::filter()->with('category')->get();
```

Using this package, you can now make a request that targets the category slug or any other field you allow to be filtered:

```
/api/books?filters[category][slug][$eq]=mystery
```

The filtered response would only include books in the category with a slug of mystery now. Purity provides various filters for things like `$in`, `$lt`, `$gt`, etc.

Purity offers the following main features to make it a robust filtering and data sorting package for Eloquent models:

- Livewire support (added in v2)
- Rename and restrict fields (added in v2)
- Various filter methods
- Simple installation and usage
- Filter by relation columns
- Custom filters
- Multi-column sort

Check out the [Purity Documentation page](https://abbasudo.github.io/laravel-purity/) for usage and setup instructions!

**Related:** [How to build an api](https://laravel-news.com/building-apis-in-laravel)

![Paul Redmond photo](https://www.gravatar.com/avatar/d9691184a54bfa1defe3dc7d625bc959) 

[Paul Redmond](/@paulredmond)

Full stack web developer. Author of Lumen Programming Guide and Docker for PHP Developers.

 [![X](https://picperf.io/https://laravel-news.com/images/x.svg) X](https://twitter.com/paulredmond)[![GitHub](https://picperf.io/https://laravel-news.com/images/github.svg) GitHub](https://github.com/paulredmond)

Filed in:

[Laravel Packages](/category/packages)