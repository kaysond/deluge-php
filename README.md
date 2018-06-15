# deluge-php - Simple php wrapper for the deluge-web json api
The deluge documentation is a little scattered. This should help people get up and running with the json api. Includes the core methods, webui methods, and also the webapi plugin (see url below)
Most functions are not tested, as they are automatically parsed from the following places:
* https://web.archive.org/web/20150423162855/http://deluge-torrent.org:80/docs/master/core/rpc.html
* https://web.archive.org/web/20150423143401/http://deluge-torrent.org:80/docs/master/modules/ui/web/json_api.html#module-deluge.ui.web.json_api
* https://github.com/idlesign/deluge-webapi

## Usage
```
include("deluge.class.php");
$deluge = new deluge("https://127.0.0.1:8112", "yourpassword");
$torrents = $deluge->getTorrents(null, null);
$status = $deluge->getTorrentStatus($torrents[0]->hash, array(), array());
$deluge->close() //Closes the cURL handle
```
Functions take a variety of arguments. Unused arguments are usually either null (equivalent to Python None) or array(). Experimentation may be necessary.

For debugging purposes, the header and body of the last request and response are stored in the public class property `last_http_transaction` (stdObj with obviously named properties)

Check the deluge-web log for details of failed requests. Failures throw php Exception's.
