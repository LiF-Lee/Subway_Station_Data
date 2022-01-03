# Subway_Station_Data

```js
const stationData = readData();

function readData() 
{
    /* Read Data from Github */
    let url = "https://raw.githubusercontent.com/EliF-Lee/Subway_Station_Data/main/stationData.json";
    let webData = org.jsoup.Jsoup.connect(url).get().text(); 
    return JSON.parse(webData);

    /* Read Data from File */
    // let path = "sdcard/example/stationData.json";
    // let fileData = FileStream.read(path);
    // return JSON.parse(fileData);
}

function getArrivalData(id) 
{
    let url = "https://subway.kakao.com/apis/station/" + id + "/arrival/filtered?lang=ko";
    let webData = org.jsoup.Jsoup.connect(url).ignoreContentType(true).get().text();
    return JSON.parse(webData);
}

function response(room, msg, sender, isGroupChat, replier, imageDB, packageName) 
{
    if (msg.startsWith("#실시간 "))
    {
        let id = stationData.stations[msg.slice(5)].id[0];
        let arrivalData = getArrivalData(id);
        replier.reply(JSON.stringify(arrivalData, null, 4));
    }
}
```
