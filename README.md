<div align="center">

## RSS/XML News Feed Parser


</div>

### Description

This code parses an XML/RSS news feed document that resembles something like this feed: http://www.webfroot.co.nz/b2/b2rss.php. It makes each title a link to the actual article. Please see the image and/or http://members.lycos.co.uk/ctsirius/parse.php !
 
### More Info
 
The only variable that usually needs to be modified is the source of the news feed. The number of bytes to read may need to be modified in the case of a VERY large news feed, which it does not completely read.

I am assuming the user is including the file, and therefore it does not echo out the XHTML header data (i.e. <html>,<head>, or &lt;body>).

The code returns the links, within a paragraph html tag.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[CT Sirius](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ct-sirius.md)
**Level**          |Advanced
**User Rating**    |4.7 (47 globes from 10 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__8-7.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ct-sirius-rss-xml-news-feed-parser__8-728/archive/master.zip)

### API Declarations

You are free to use it and redistribute unmodified.


### Source Code

```
<?
//The file to Parse, (i.e) Web Address.
$file = "http://www.webfroot.co.nz/b2/b2rss.php";
//Number of Bytes to Read. 10000 Should be Enough.
//Increase only if it does not read the entire file.
$byte = "100000";
//No more editing.
$ofile = @fopen("$file", "r");
$contents = @fread ($ofile, $byte);
@fclose($ofile);
if(!$contents)
{
echo "<p>\nUnable to Get XML/RSS data. Fatal Error.\n</p>";
exit;
}
preg_match_all ("'<title>(.*?)</title>'si", $contents, $titles);
preg_match_all ("'<link>(.*?)</link>'si", $contents, $link);
$count = count($titles[1]);
$link = $link[1];
$titles = $titles[1];
echo "<p>\n";
for($i = 0; $i <= $count; $i++)
{
echo "<a href=\"$link[$i]\">$titles[$i]</a>\n<br />\n";
}
echo "</p>";
?>
```

