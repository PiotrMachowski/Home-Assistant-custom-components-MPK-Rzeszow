[![buymeacoffee_badge](https://img.shields.io/badge/Donate-Buy%20Me%20a%20Coffee-ff813f?style=flat)](https://www.buymeacoffee.com/PiotrMachowski)
[![paypalme_badge](https://img.shields.io/badge/Donate-PayPal-0070ba?style=flat)](https://paypal.me/PiMachowski)

This sensor use unofficial API provided by MPK Rzeszów.

## Configuration options

| Key | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `name` | `string` | `False` | `MPK Rzeszów` | Name of sensor |
| `stops` | `list` | `True` | - | List of stop configurations |

### Stop configuration

| Key | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `id` | `positive integer` | `True` | - | ID of a stop |
| `name` | `string` | `False` | id | Name of a stop |
| `lines` | `list` | `False` | all available | List of monitored lines. |
| `directions` | `list` | `False` | all available | List of monitored directions. |

## Example usage

```
sensor:
  - platform: mpk_rzeszow
      stops:
        - id: 875
          lines:
            - "13"          
            - "2"          
        - id: 18
          directions:
            - "Obr. Poczty Gdańskiej"
```

## Hints

* Value for `stop_id` can be retrieved from [*E-INFO Rzeszów*](http://einfo.erzeszow.pl/). After choosing a desired stop open its electronical table. `stop_id` is a number visibile in URL.

* These sensors provides attributes which can be used in [*HTML card*](https://github.com/PiotrMachowski/Home-Assistant-Lovelace-HTML-card) or [*HTML Template card*](https://github.com/PiotrMachowski/Home-Assistant-Lovelace-HTML-Template-card): `html_timetable`, `html_departures`
  * HTML card:
    ```yaml
    - type: custom:html-card
      title: 'MPK'
      content: |
        <big><center>Timetable</center></big>
        [[ sensor.mpk_rzeszow_875.attributes.html_timetable ]]
        <big><center>Departures</center></big>
        [[ sensor.mpk_rzeszow_18.attributes.html_departures ]]
    ```
  * HTML Template card:
    ```yaml
    - type: custom:html-template-card
      title: 'MPK'
      ignore_line_breaks: true
      content: |
        <big><center>Timetable</center></big></br>
        {{ state_attr('sensor.mpk_rzeszow_875','html_timetable') }}
        </br><big><center>Departures</center></big></br>
        {{ state_attr('sensor.mpk_rzeszow_18','html_departures') }}
    ```

<a href="https://www.buymeacoffee.com/PiotrMachowski" target="_blank"><img src="https://bmc-cdn.nyc3.digitaloceanspaces.com/BMC-button-images/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>
