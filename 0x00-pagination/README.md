0x00. Pagination
=

<h2>REST API Design: Filtering, Sorting, and Pagination</h2>

<h2>Filtering</h2>

URL parameters is the easiest way to add basic filtering to REST APIs. If you have an /items endpoint which are items for sale, you can filter via the property name such as GET /items?state=active or GET /items?state=active&seller_id=1234.

URL parameters only have a key and a value but filters are composed of three components

* The property or field name

* The operator such as eq, lte, gte

* The filter value

                 var qs = require('qs');
                 var assert = require('assert');

                assert.deepEqual(qs.parse('price[gte]=10&price[lte]=100'), {
                       price: {
                            gte: 10,
                            lte: 100
               }
            });


<h2>Pagination</h2>

Most endpoints that returns a list of entities will need to have some sort of pagination.Without pagination, a simple search could return millions or even billions of hits causing extraneous network traffic.Paging requires an implied ordering. By default this may be the item’s unique identifier, but can be other ordered fields such as a created date.


                SELECT
                    *

                FROM
                   Items
                ORDER BY Id
                LIMIT 20
                OFFSET 40;

<h2>Sorting</h2>


sorting is an important feature for any API endpoint that returns a lot of data. If you’re returning a list of users, your API users may want to sort by last modified date or by email. To enable sorting, many APIs add a sort or sort_by URL parameter that can take a field name as the value.API designs give the flexibility to specify ascending or descending order. Like filters, specifying the order requires encoding three components into a key/value pair.

                  SELECT
                      email
                  FROM
                     Items
                  ORDER BY Last_Modified DESC, Email ASC
                  LIMIT 20


Hypermedia as the Engine of Application State (HATEOAS)
=

HATEOAS : is a constraint of the REST application architecture that distinguishes it from other network application architectures.

With HATEOAS, a client interacts with a network application whose application servers provide information dynamically through hypermedia. A REST client needs little to no prior knowledge about how to interact with an application or server beyond a generic understanding of hypermedia.