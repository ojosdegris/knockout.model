# Knockout.model plugin
Copyright 2011, Alisson Cavalcante Agiani
Licensed under the MIT license.
http://github.com/thelinuxlich/knockout.model/MIT-LICENSE.txt
Date: Fri Mar 04 14:00:29 2011 -0300

## Files:
* knockout.model.js

## Dependencies:
* jQuery 1.4.2+
* reqman.js at https://github.com/thelinuxlich/reqman.js
* Knockout 1.1+

## Howto
* This plugin was created with Coffeescript class approach, so you should use it too or you'll have to write a lot of ugly javascript

## Example(see docs for more details):
    class @Employee extends KnockoutModel

        constructor: (defaults) ->
            @id = ko.observable ""
            @name = ko.observable ""
            @surname = ko.observable ""
            @fullname = ko.dependentObservable(-> @name() + " " + @surname()), @
            @birth_date = ko.observable ""
            @address = ko.observable ""
            @phone = ko.observable ""
            urls =
                "get": "http://#{window.location.host}/employees"
                "post": "http://#{window.location.host}/employees/post"
                "put": "http://#{window.location.host}/employees/put"
                "delete": "http://#{window.location.host}/employees/delete"
            super(defaults,urls)

        validate: ->
            @name() isnt "" and @surname() isnt "" and @birth_date() isnt "" and
                    @address() isnt ""
