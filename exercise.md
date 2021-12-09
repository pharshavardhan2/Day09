### Q)a)
- Used https://restcountries.com/v3.1/all api
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://restcountries.com/v3.1/all");

xhr.onload = function() {
  if(xhr.status >= 200 && xhr.status < 300) {
    let data = JSON.parse(this.responseText);
    let asianCountries = data.filter((country) => {
      return country.region === "Asia";
    });
    let asianStr = "";
    for(let country of asianCountries) {
      asianStr += country.name.common + ", ";
    }
    console.log(asianStr);
  } else {
    console.log("Error");
  }
};

xhr.send();
```
- Output
> Jordan, Turkmenistan, Iran, United Arab Emirates, Turkey, Japan, Kazakhstan, Palestine, Oman, Thailand, Timor-Leste, Armenia, Kuwait, Georgia, Cambodia, Israel, Malaysia, Singapore, China, Sri Lanka, Pakistan, Hong Kong, Lebanon, Tajikistan, Macau, Vietnam, Myanmar, Philippines, Qatar, Yemen, Mongolia, Brunei, Nepal, Maldives, Syria, Kyrgyzstan, Uzbekistan, Bahrain, Indonesia, Bangladesh, South Korea, North Korea, Taiwan, Iraq, Bhutan, Afghanistan, India, Saudi Arabia, Azerbaijan, Laos

### Q)b)
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://restcountries.com/v3.1/all");

xhr.onload = function() {
  if(xhr.status >= 200 && xhr.status < 300) {
    let data = JSON.parse(this.responseText);
    let lessPeopleCountries = data.filter((country) => {
      return country.population < 200000;
    });
    let countryStr = "";
    for(let country of lessPeopleCountries) {
      countryStr += country.name.common + ", ";
    }
    console.log(countryStr);
  } else {
    console.log("Error");
  }
};

xhr.send();
```
- Output
> San Marino, Christmas Island, Vatican City, Seychelles, Guam, Antarctica, Åland Islands, Tokelau, Turks and Caicos Islands, Palau, French Southern and Antarctic Lands, Bouvet Island, British Virgin Islands, Heard Island and McDonald Islands, Sint Maarten, Norfolk Island, Northern Mariana Islands, Greenland, British Indian Ocean Territory, American Samoa, South Georgia, Saint Martin, Anguilla, Cayman Islands, Tonga, Curaçao, Saint Vincent and the Grenadines, Grenada, Marshall Islands, Saint Lucia, Gibraltar, Niue, Samoa, Antigua and Barbuda, Bermuda, Saint Pierre and Miquelon, Liechtenstein, Guernsey, Nauru, Kiribati, Saint Kitts and Nevis, United States Minor Outlying Islands, Pitcairn Islands, Aruba, Saint Helena, Ascension and Tristan da Cunha, Montserrat, Falkland Islands, Svalbard and Jan Mayen, Wallis and Futuna, Isle of Man, United States Virgin Islands, Faroe Islands, Jersey, Saint Barthélemy, Monaco, Cocos (Keeling) Islands, Dominica, Tuvalu, Caribbean Netherlands, Micronesia, Cook Islands, Andorra

### Q)c)
- if capital or flag is not present for a country then I printed "None" for that.
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://restcountries.com/v3.1/all");

xhr.onload = function() {
  if(xhr.status >= 200 && xhr.status < 300) {
    let data = JSON.parse(this.responseText);
    let countryStr = "";
    data.forEach((country) => {
      let name = country.name.common;
      let capital = country.capital ? country.capital.toString() : "None";
      let flag = country.flag ? country.flag : "None";
      countryStr += `${name}, ${capital}, ${flag}\n`;
    });
    console.log(countryStr);
  } else {
    console.log("Error");
  }
};

xhr.send();
```
- Output
> Kenya, Nairobi, 🇰🇪  
San Marino, City of San Marino, 🇸🇲  
French Polynesia, Papeetē, 🇵🇫  
Sierra Leone, Freetown, 🇸🇱  
Madagascar, Antananarivo, 🇲🇬  
Nigeria, Abuja, 🇳🇬  
Jordan, Amman, 🇯🇴  
Libya, Tripoli, 🇱🇾  
Guyana, Georgetown, 🇬🇾  
Mexico, Mexico City, 🇲🇽  
Turkmenistan, Ashgabat, 🇹🇲  
Christmas Island, Flying Fish Cove, 🇨🇽  
Panama, Panama City, 🇵🇦  
Vatican City, Vatican City, 🇻🇦  
Seychelles, Victoria, 🇸🇨  
Algeria, Algiers, 🇩🇿  
Guam, Hagåtña, 🇬🇺  
Sweden, Stockholm, 🇸🇪  
Antarctica, None, 🇦🇶  
Switzerland, Bern, 🇨🇭  
Ethiopia, Addis Ababa, 🇪🇹  
Somalia, Mogadishu, 🇸🇴  
France, Paris, 🇫🇷  
Russia, Moscow, 🇷🇺  
Western Sahara, El Aaiún, 🇪🇭  
Åland Islands, Mariehamn, 🇦🇽  
Tokelau, Fakaofo, 🇹🇰  
Chad, N'Djamena, 🇹🇩  
Trinidad and Tobago, Port of Spain, 🇹🇹  
Central African Republic, Bangui, 🇨🇫  
North Macedonia, Skopje, 🇲🇰  
El Salvador, San Salvador, 🇸🇻  
Turks and Caicos Islands, Cockburn Town, 🇹🇨  
Kosovo, Pristina, 🇽🇰  
Colombia, Bogotá, 🇨🇴  
Palau, Ngerulmud, 🇵🇼  
Iran, Tehran, 🇮🇷  
French Southern and Antarctic Lands, Port-aux-Français, 🇹🇫  
Bouvet Island, None, 🇧🇻  
British Virgin Islands, Road Town, 🇻🇬  
United Arab Emirates, Abu Dhabi, 🇦🇪  
South Africa, Pretoria,Bloemfontein,Cape Town, 🇿🇦  
Czechia, Prague, 🇨🇿  
Hungary, Budapest, 🇭🇺  
Peru, Lima, 🇵🇪  
Benin, Porto-Novo, 🇧🇯  
South Sudan, Juba, 🇸🇸  
Heard Island and McDonald Islands, None, 🇭🇲  
Solomon Islands, Honiara, 🇸🇧  
Sint Maarten, Philipsburg, 🇸🇽  
Turkey, Ankara, 🇹🇷  
Ireland, Dublin, 🇮🇪  
Botswana, Gaborone, 🇧🇼  
Haiti, Port-au-Prince, 🇭🇹  
Japan, Tokyo, 🇯🇵  
Norfolk Island, Kingston, 🇳🇫  
Sudan, Khartoum, 🇸🇩  
Uganda, Kampala, 🇺🇬  
Kazakhstan, Nur-Sultan, 🇰🇿  
Northern Mariana Islands, Saipan, 🇲🇵  
Moldova, Chișinău, 🇲🇩  
Paraguay, Asunción, 🇵🇾  
Estonia, Tallinn, 🇪🇪  
Greenland, Nuuk, 🇬🇱  
Palestine, Ramallah, 🇵🇸  
Finland, Helsinki, 🇫🇮  
São Tomé and Príncipe, São Tomé, 🇸🇹  
Honduras, Tegucigalpa, 🇭🇳  
Dominican Republic, Santo Domingo, 🇩🇴  
British Indian Ocean Territory, Diego Garcia, 🇮🇴  
Rwanda, Kigali, 🇷🇼  
Comoros, Moroni, 🇰🇲  
Oman, Muscat, 🇴🇲  
Portugal, Lisbon, 🇵🇹  
American Samoa, Pago Pago, 🇦🇸  
Thailand, Bangkok, 🇹🇭  
Timor-Leste, Dili, 🇹🇱  
Armenia, Yerevan, 🇦🇲  
Kuwait, Kuwait City, 🇰🇼  
South Georgia, King Edward Point, 🇬🇸  
Saint Martin, Marigot, 🇲🇫  
Georgia, Tbilisi, 🇬🇪  
Burundi, Gitega, 🇧🇮  
Anguilla, The Valley, 🇦🇮  
Cambodia, Phnom Penh, 🇰🇭  
Lesotho, Maseru, 🇱🇸  
Cayman Islands, George Town, 🇰🇾  
Vanuatu, Port Vila, 🇻🇺  
Bolivia, Sucre, 🇧🇴  
United Kingdom, London, 🇬🇧  
Tonga, Nuku'alofa, 🇹🇴  
Spain, Madrid, 🇪🇸  
Israel, Jerusalem, 🇮🇱  
Malaysia, Kuala Lumpur, 🇲🇾  
Curaçao, Willemstad, 🇨🇼  
DR Congo, Kinshasa, 🇨🇩  
Cuba, Havana, 🇨🇺  
Djibouti, Djibouti, 🇩🇯  
Chile, Santiago, 🇨🇱  
Bosnia and Herzegovina, Sarajevo, 🇧🇦  
Singapore, Singapore, 🇸🇬  
French Guiana, Cayenne, 🇬🇫  
Suriname, Paramaribo, 🇸🇷  
Eswatini, Mbabane, 🇸🇿  
Belgium, Brussels, 🇧🇪  
China, Beijing, 🇨🇳  
Saint Vincent and the Grenadines, Kingstown, 🇻🇨  
Nicaragua, Managua, 🇳🇮  
Canada, Ottawa, 🇨🇦  
Togo, Lomé, 🇹🇬  
Ivory Coast, Yamoussoukro, 🇨🇮  
Slovenia, Ljubljana, 🇸🇮  
Sri Lanka, Sri Jayawardenepura Kotte, 🇱🇰  
Greece, Athens, 🇬🇷  
Jamaica, Kingston, 🇯🇲  
Italy, Rome, 🇮🇹  
Croatia, Zagreb, 🇭🇷  
New Caledonia, Nouméa, 🇳🇨  
Pakistan, Islamabad, 🇵🇰  
Hong Kong, City of Victoria, 🇭🇰  
Latvia, Riga, 🇱🇻  
Lebanon, Beirut, 🇱🇧  
Mauritius, Port Louis, 🇲🇺  
Guinea, Conakry, 🇬🇳  
Republic of the Congo, Brazzaville, 🇨🇬  
Grenada, St. George's, 🇬🇩  
Eritrea, Asmara, 🇪🇷  
Barbados, Bridgetown, 🇧🇧  
Tajikistan, Dushanbe, 🇹🇯  
Burkina Faso, Ouagadougou, 🇧🇫  
Macau, None, 🇲🇴  
Marshall Islands, Majuro, 🇲🇭  
Belarus, Minsk, 🇧🇾  
Mayotte, Mamoudzou, 🇾🇹  
Zambia, Lusaka, 🇿🇲  
Iceland, Reykjavik, 🇮🇸  
Saint Lucia, Castries, 🇱🇨  
Vietnam, Hanoi, 🇻🇳  
Brazil, Brasília, 🇧🇷  
Myanmar, Naypyidaw, 🇲🇲  
Senegal, Dakar, 🇸🇳  
Slovakia, Bratislava, 🇸🇰  
Philippines, Manila, 🇵🇭  
Albania, Tirana, 🇦🇱  
Montenegro, Podgorica, 🇲🇪  
Gabon, Libreville, 🇬🇦  
Qatar, Doha, 🇶🇦  
Venezuela, Caracas, 🇻🇪  
Gibraltar, Gibraltar, 🇬🇮  
Niue, Alofi, 🇳🇺  
Samoa, Apia, 🇼🇸  
Antigua and Barbuda, Saint John's, 🇦🇬  
Liberia, Monrovia, 🇱🇷  
Belize, Belmopan, 🇧🇿  
Equatorial Guinea, Malabo, 🇬🇶  
Yemen, Sana'a, 🇾🇪  
Tanzania, Dodoma, 🇹🇿  
Australia, Canberra, 🇦🇺  
Bermuda, Hamilton, 🇧🇲  
Saint Pierre and Miquelon, Saint-Pierre, 🇵🇲  
Mongolia, Ulan Bator, 🇲🇳  
Malta, Valletta, 🇲🇹  
Luxembourg, Luxembourg, 🇱🇺  
Liechtenstein, Vaduz, 🇱🇮  
Poland, Warsaw, 🇵🇱  
Brunei, Bandar Seri Begawan, 🇧🇳  
Nepal, Kathmandu, 🇳🇵  
Argentina, Buenos Aires, 🇦🇷  
Guernsey, St. Peter Port, 🇬🇬  
Maldives, Malé, 🇲🇻  
Malawi, Lilongwe, 🇲🇼  
Nauru, Yaren, 🇳🇷  
Syria, Damascus, 🇸🇾  
Kiribati, South Tarawa, 🇰🇮  
Martinique, Fort-de-France, 🇲🇶  
Kyrgyzstan, Bishkek, 🇰🇬  
Saint Kitts and Nevis, Basseterre, 🇰🇳  
Uzbekistan, Tashkent, 🇺🇿  
Netherlands, Amsterdam, 🇳🇱  
United States Minor Outlying Islands, None, 🇺🇲  
Niger, Niamey, 🇳🇪  
Bahrain, Manama, 🇧🇭  
Indonesia, Jakarta, 🇮🇩  
Guadeloupe, Basse-Terre, 🇬🇵  
Réunion, Saint-Denis, 🇷🇪  
Pitcairn Islands, Adamstown, 🇵🇳  
Aruba, Oranjestad, 🇦🇼  
Bangladesh, Dhaka, 🇧🇩  
Guatemala, Guatemala City, 🇬🇹  
Bahamas, Nassau, 🇧🇸  
Uruguay, Montevideo, 🇺🇾  
Morocco, Rabat, 🇲🇦  
Germany, Berlin, 🇩🇪  
Saint Helena, Ascension and Tristan da Cunha, Jamestown, 🇸🇭  
Montserrat, Plymouth, 🇲🇸  
United States, Washington, D.C., 🇺🇸  
Falkland Islands, Stanley, 🇫🇰  
Bulgaria, Sofia, 🇧🇬  
Papua New Guinea, Port Moresby, 🇵🇬  
Costa Rica, San José, 🇨🇷  
Ecuador, Quito, 🇪🇨  
Svalbard and Jan Mayen, Longyearbyen, 🇸🇯  
Fiji, Suva, 🇫🇯  
South Korea, Seoul, 🇰🇷  
Puerto Rico, San Juan, 🇵🇷  
Wallis and Futuna, Mata-Utu, 🇼🇫  
North Korea, Pyongyang, 🇰🇵  
Taiwan, Taipei, 🇹🇼  
Isle of Man, Douglas, 🇮🇲  
United States Virgin Islands, Charlotte Amalie, 🇻🇮  
Lithuania, Vilnius, 🇱🇹  
Angola, Luanda, 🇦🇴  
Tunisia, Tunis, 🇹🇳  
Faroe Islands, Tórshavn, 🇫🇴  
Ghana, Accra, 🇬🇭  
Iraq, Baghdad, 🇮🇶  
New Zealand, Wellington, 🇳🇿  
Serbia, Belgrade, 🇷🇸  
Bhutan, Thimphu, 🇧🇹  
Romania, Bucharest, 🇷🇴  
Afghanistan, Kabul, 🇦🇫  
India, New Delhi, 🇮🇳  
Denmark, Copenhagen, 🇩🇰  
Jersey, Saint Helier, 🇯🇪  
Saudi Arabia, Riyadh, 🇸🇦  
Saint Barthélemy, Gustavia, 🇧🇱  
Guinea-Bissau, Bissau, 🇬🇼  
Norway, Oslo, 🇳🇴  
Monaco, Monaco, 🇲🇨  
Cocos (Keeling) Islands, West Island, 🇨🇨  
Egypt, Cairo, 🇪🇬  
Cyprus, Nicosia, 🇨🇾  
Dominica, Roseau, 🇩🇲  
Azerbaijan, Baku, 🇦🇿  
Zimbabwe, Harare, 🇿🇼  
Tuvalu, Funafuti, 🇹🇻  
Mali, Bamako, 🇲🇱  
Mauritania, Nouakchott, 🇲🇷  
Ukraine, Kyiv, 🇺🇦  
Cameroon, Yaoundé, 🇨🇲  
Caribbean Netherlands, Kralendijk, None  
Micronesia, Palikir, 🇫🇲  
Mozambique, Maputo, 🇲🇿  
Namibia, Windhoek, 🇳🇦  
Gambia, Banjul, 🇬🇲  
Cook Islands, Avarua, 🇨🇰  
Cape Verde, Praia, 🇨🇻  
Laos, Vientiane, 🇱🇦  
Austria, Vienna, 🇦🇹  
Andorra, Andorra la Vella, 🇦🇩  

### Q)d)
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://restcountries.com/v3.1/all");

xhr.onload = function() {
  if(xhr.status >= 200 && xhr.status < 300) {
    let data = JSON.parse(this.responseText);
    let totalPopulation = data.reduce((a, b) => {
      return a + b.population;
    }, 0);
    console.log(totalPopulation);
  } else {
    console.log("Error");
  }
};

xhr.send();
```
- Output
> 7770055907

### Q)e)
```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://restcountries.com/v3.1/all");

xhr.onload = function() {
  if(xhr.status >= 200 && xhr.status < 300) {
    let data = JSON.parse(this.responseText);
    let usdCountries = data.filter((country) => {
      return country.currencies ? "USD" in country.currencies : false;
    });
    let countryNames = usdCountries.map((country) => {
      return country.name.common;
    })
    console.log(countryNames.toString());
  } else {
    console.log("Error");
  }
};

xhr.send();
```
- Output
> Panama,Guam,El Salvador,Turks and Caicos Islands,Palau,British Virgin Islands,Northern Mariana Islands,British Indian Ocean Territory,American Samoa,Timor-Leste,Cambodia,Marshall Islands,United States Minor Outlying Islands,Bahamas,United States,Ecuador,Puerto Rico,United States Virgin Islands,Caribbean Netherlands,Micronesia

