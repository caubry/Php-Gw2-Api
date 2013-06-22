PhpGw2Api
=========

>PhpGw2Api is a PHP wrapper for the GW2 API.

Requirements
-
- PHP 5.3+
- cURL

Usage
-

    require_once 'src/PhpGw2Api/Service.php';
    
    // Instatiate a new service object and specify cache path and TTL settings
    $service = new PhpGw2Api\Service(__DIR__ . '/cache', 3600);
    
    // Set how to return the JSON
    $service->returnAssoc(true);
    
    // Query 
    $items = $service->getItems();
    
    // Play around
    $itemId = $items['items'][50];
    $item = $service->getItemDetails(array('item_id' => $itemId));

    var_dump($item);

Examples
-

Examples of use can be found [here](http://www.gw2dashboard.net/)

Caching
-
If a cache directory is specified, the JSON response will be cached locally with the specified lifetime, or a default of 3600 seconds.
You can specify cache settings in the following ways:

Upon instatiation:

    $service = new PhpGw2Api\Service(__DIR__ . '/cache', 3600);

Using the fluent interface:

    $service->setCacheDirectory(__DIR__ . '/cache')
            ->setCacheTtl(120)
            ->getItems();

Additionally, TTL may be specified on a per request basis:

    $service->getItems(array(), 60);

Reference
-

The following draws reference from [https://forum-en.guildwars2.com/forum/community/api/API-Documentation](https://forum-en.guildwars2.com/forum/community/api/API-Documentation)

### getEvents

*Optional parameters: world_id, map_id, event_id*

    $service->getEvents(array('world_id' => 1001));
    
### getEventNames

*Optional parameters: lang*

    $service->getEventNames(array('lang' => 'fr'));

### getEventDetails

*Optional parameters: event_id, lang*

    $service->getEventDetails(array('event_id' => 'EED8A79F-B374-4AE6-BA6F-B7B98D9D7142', 'lang' => 'fr'));
    
### getMapNames

*Optional parameters: lang*

    $service->getMapNames(array('lang' => 'fr'));
    
### getWorldNames

*Optional parameters: lang*

    $service->getWorldNames(array('lang' => 'fr'));
    
### getMatches

    $service->getMatches();
    
### getMatchDetails

*Requred parameters: match_id*

    $service->getMatchDetails(array('match_id' => '2-3'));
    
### getObjectiveNames

*Optional parameters: lang*

    $service->getObjectiveNames(array('lang' => 'fr'));
    
### getItems

    $service->getItems();
    
### getItemDetails

*Required parameters: item_id*
*Optional parameters: lang*

    $service->getItemDetails(array('item_id' => 15728));
    
### getRecipes

    $service->getRecipes();
    
### getRecipeDetails

*Required parameters: recipe_id*

    $service->getRecipeDetails(array('recipe_id' => 984));

### getGuildDetails

*Required parameters: guild_id or guild_name*

    $service->getGuildDetails(array('guild_name' => 'In Time'));

### getBuild

    $service->getBuild();

### getColours

*Optional parameters: lang*

    $service->getColours(array('lang' => 'fr'));

### getColors

Alias of `getColours()` for our American friends.

*Optional parameters: lang*

    $service->getColors(array('lang' => 'fr'));

### getContinents

*Optional parameters: lang*

    $service->getContinents(array('lang' => 'fr'));

### getMaps

*Optional parameters: lang, map_id*

    $service->getMaps(array('lang' => 'fr', 'map_id' => 80));

### getMapFloor

*Required parameters: continent_id, floor*
*Optional parameters: lang*

    $service->getMapFloor(array('continent_id' => 1, 'floor' => 1, 'lang' => 'fr'));

License
- 
Released under the [MIT licence](http://opensource.org/licenses/MIT)

Feedback & contribution
-
Feedback and contribution are welcomed!
