# Copy paste cmds

Open browser console, then

## Copy the pipeline

```
JSON.stringify(angular.element(document.getElementsByClassName('addProcessor')[0]).scope().dataset.processors).replace(/\\/g, '\\\\').replace(/'/g, "\\'")
```

Get the JSON value within the double quotes

## Paste pipeline

Paste it by replacing `<ctrl-v>` by your JSON array
```
angular.element(document.getElementsByClassName('addProcessor')[0]).scope().dataset.processors = JSON.parse('<ctrl-v>')
```