# User Queries

User queries are a type of [element query](README.md) used to fetch your project’s users.

They are implemented by <api:craft\elements\db\UserQuery>, and the elements returned by them will be of type <api:craft\elements\User>.

## Creating User Queries

You can create a new user query from Twig by calling `craft.users()`, or from PHP by calling <api:craft\elements\User::find()>.

::: code
```twig
{% set authors = craft.users()
    .group('authors')
    .all() %}

<ul>
    {% for author in authors %}
        <li><a href="{{ url('authors/'~author.id) }}">{{ author.name }}</a></li>
    {% endfor %}
</ul>
```
```php
/** @var \craft\elements\User[] $authors */
$authors = \craft\elements\User::find()
    ->group('authors')
    ->all();
```
:::

## Parameters

User queries support the following parameters:

<!-- BEGIN PARAMS -->

### `admin`

Allowed types

:   [boolean](http://php.net/language.types.boolean), [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$admin](api:craft\elements\db\UserQuery::$admin)

Settable by

:   [admin()](api:craft\elements\db\UserQuery::admin())



Whether to only return users that are admins.


::: code
```twig
{# fetch all the admins #}
{% set admins = craft.users()
    .admin()
    .all()%}

{# fetch all the non-admins #}
{% set nonAdmins = craft.users()
    .admin(false)
    .all() %}
```

```php
// fetch all the admins
$admins = \craft\elements\User::find()
    ->admin(true)
    ->all();

// fetch all the non-admins
$nonAdmins = \craft\elements\User::find()
    ->admin(false)
    ->all();
```
:::
### `archived`

Allowed types

:   [boolean](http://php.net/language.types.boolean)

Defined by

:   [ElementQuery::$archived](api:craft\elements\db\ElementQuery::$archived)

Settable by

:   [archived()](api:craft\elements\db\ElementQuery::archived())



Whether to return only archived elements.


### `asArray`

Allowed types

:   [boolean](http://php.net/language.types.boolean)

Defined by

:   [ElementQuery::$asArray](api:craft\elements\db\ElementQuery::$asArray)

Settable by

:   [asArray()](api:craft\elements\db\ElementQuery::asArray())



Whether to return each element as an array. If false (default), an object
of [$elementType](https://docs.craftcms.com/api/v3/craft-elements-db-elementquery.html#property-elementtype) will be created to represent each element.


### `can`

Allowed types

:   [string](http://php.net/language.types.string), [integer](http://php.net/language.types.integer), [false](http://php.net/language.types.boolean), [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$can](api:craft\elements\db\UserQuery::$can)

Settable by

:   [can()](api:craft\elements\db\UserQuery::can())



The permission that the resulting users must have.


::: code
```twig
{# fetch users with CP access #}
{% set admins = craft.users()
    .can('accessCp')
    .all() %}
```

```php
// fetch users with CP access
$admins = \craft\elements\User::find()
    ->can('accessCp')
    ->all();
```
:::
### `dateCreated`

Allowed types

:   `mixed`

Defined by

:   [ElementQuery::$dateCreated](api:craft\elements\db\ElementQuery::$dateCreated)

Settable by

:   [dateCreated()](api:craft\elements\db\ElementQuery::dateCreated())



When the resulting elements must have been created.


### `dateUpdated`

Allowed types

:   `mixed`

Defined by

:   [ElementQuery::$dateUpdated](api:craft\elements\db\ElementQuery::$dateUpdated)

Settable by

:   [dateUpdated()](api:craft\elements\db\ElementQuery::dateUpdated())



When the resulting elements must have been last updated.


### `email`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$email](api:craft\elements\db\UserQuery::$email)

Settable by

:   [email()](api:craft\elements\db\UserQuery::email())



The email address that the resulting users must have.


### `enabledForSite`

Allowed types

:   [boolean](http://php.net/language.types.boolean)

Defined by

:   [ElementQuery::$enabledForSite](api:craft\elements\db\ElementQuery::$enabledForSite)

Settable by

:   [enabledForSite()](api:craft\elements\db\ElementQuery::enabledForSite())



Whether the elements must be enabled for the chosen site.


### `firstName`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$firstName](api:craft\elements\db\UserQuery::$firstName)

Settable by

:   [firstName()](api:craft\elements\db\UserQuery::firstName())



The first name that the resulting users must have.


### `fixedOrder`

Allowed types

:   [boolean](http://php.net/language.types.boolean)

Defined by

:   [ElementQuery::$fixedOrder](api:craft\elements\db\ElementQuery::$fixedOrder)

Settable by

:   [fixedOrder()](api:craft\elements\db\ElementQuery::fixedOrder())



Whether results should be returned in the order specified by [id()](https://docs.craftcms.com/api/v3/craft-elements-db-elementquery.html#method-id).


### `groupId`

Allowed types

:   [integer](http://php.net/language.types.integer), [integer](http://php.net/language.types.integer)[], [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$groupId](api:craft\elements\db\UserQuery::$groupId)

Settable by

:   [group()](api:craft\elements\db\UserQuery::group()), [groupId()](api:craft\elements\db\UserQuery::groupId())



The user group ID(s) that the resulting users must belong to.


::: code
```twig
{# fetch the authors #}
{% set admins = craft.users()
    .group('authors')
    .all() %}
```

```php
// fetch the authors
$admins = \craft\elements\User::find()
    ->group('authors')
    ->all();
```
:::
### `id`

Allowed types

:   [integer](http://php.net/language.types.integer), [integer](http://php.net/language.types.integer)[], [false](http://php.net/language.types.boolean), [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$id](api:craft\elements\db\ElementQuery::$id)

Settable by

:   [id()](api:craft\elements\db\ElementQuery::id())



The element ID(s). Prefix IDs with `'not '` to exclude them.


### `inReverse`

Allowed types

:   [boolean](http://php.net/language.types.boolean)

Defined by

:   [ElementQuery::$inReverse](api:craft\elements\db\ElementQuery::$inReverse)

Settable by

:   [inReverse()](api:craft\elements\db\ElementQuery::inReverse())



Whether the results should be queried in reverse.


### `lastLoginDate`

Allowed types

:   `mixed`

Defined by

:   [UserQuery::$lastLoginDate](api:craft\elements\db\UserQuery::$lastLoginDate)

Settable by

:   [lastLoginDate()](api:craft\elements\db\UserQuery::lastLoginDate())



The date that the resulting users must have last logged in.


### `lastName`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$lastName](api:craft\elements\db\UserQuery::$lastName)

Settable by

:   [lastName()](api:craft\elements\db\UserQuery::lastName())



The last name that the resulting users must have.


### `ref`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$ref](api:craft\elements\db\ElementQuery::$ref)

Settable by

:   [ref()](api:craft\elements\db\ElementQuery::ref())



The reference code(s) used to identify the element(s).

This property is set when accessing elements via their reference tags, e.g. `{entry:section/slug}`.


### `relatedTo`

Allowed types

:   [integer](http://php.net/language.types.integer), [array](http://php.net/language.types.array), [craft\base\ElementInterface](api:craft\base\ElementInterface), [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$relatedTo](api:craft\elements\db\ElementQuery::$relatedTo)

Settable by

:   [relatedTo()](api:craft\elements\db\ElementQuery::relatedTo())



The element relation criteria.

See [Relations](https://docs.craftcms.com/v3/relations.html) for supported syntax options.


### `search`

Allowed types

:   [string](http://php.net/language.types.string), [array](http://php.net/language.types.array), [craft\search\SearchQuery](api:craft\search\SearchQuery), [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$search](api:craft\elements\db\ElementQuery::$search)

Settable by

:   [search()](api:craft\elements\db\ElementQuery::search())



The search term to filter the resulting elements by.

See [Searching](https://docs.craftcms.com/v3/searching.html) for supported syntax options.


### `siteId`

Allowed types

:   [integer](http://php.net/language.types.integer), [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$siteId](api:craft\elements\db\ElementQuery::$siteId)

Settable by

:   [site()](api:craft\elements\db\ElementQuery::site()), [siteId()](api:craft\elements\db\ElementQuery::siteId())



The site ID that the elements should be returned in.


### `slug`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$slug](api:craft\elements\db\ElementQuery::$slug)

Settable by

:   [slug()](api:craft\elements\db\ElementQuery::slug())



The slug that resulting elements must have.


### `status`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$status](api:craft\elements\db\ElementQuery::$status)

Settable by

:   [status()](api:craft\elements\db\ElementQuery::status())



The status(es) that the resulting elements must have.


### `title`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$title](api:craft\elements\db\ElementQuery::$title)

Settable by

:   [title()](api:craft\elements\db\ElementQuery::title())



The title that resulting elements must have.


### `uid`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$uid](api:craft\elements\db\ElementQuery::$uid)

Settable by

:   [uid()](api:craft\elements\db\ElementQuery::uid())



The element UID(s). Prefix UIDs with `'not '` to exclude them.


### `uri`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$uri](api:craft\elements\db\ElementQuery::$uri)

Settable by

:   [uri()](api:craft\elements\db\ElementQuery::uri())



The URI that the resulting element must have.


### `username`

Allowed types

:   [string](http://php.net/language.types.string), [string](http://php.net/language.types.string)[], [null](http://php.net/language.types.null)

Defined by

:   [UserQuery::$username](api:craft\elements\db\UserQuery::$username)

Settable by

:   [username()](api:craft\elements\db\UserQuery::username())



The username that the resulting users must have.


### `with`

Allowed types

:   [string](http://php.net/language.types.string), [array](http://php.net/language.types.array), [null](http://php.net/language.types.null)

Defined by

:   [ElementQuery::$with](api:craft\elements\db\ElementQuery::$with)

Settable by

:   [with()](api:craft\elements\db\ElementQuery::with()), [andWith()](api:craft\elements\db\ElementQuery::andWith())



The eager-loading declaration.

See [Eager-Loading Elements](https://docs.craftcms.com/v3/eager-loading-elements.html) for supported syntax options.



<!-- END PARAMS -->
