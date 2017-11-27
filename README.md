# How to use

```html
<link href="/select2/select2.min.css" rel="stylesheet" />

...................
...................

<script type="text/javascript" src="/select2/select2.min.js"></script>
<script type="text/javascript" src="/select2/i18n/zh-CN.js"></script>
<select id="select_id">
   
</select>

```
You need script like this:
```javascript
<script>
 
#1. added maximumDisplayOptionsLength options in select2
# format of data_info: [{"id":"100","text":"JasonLi","code":"li"},{"id":"101","text":"Tomas","code":"tt"}]

	$('#select_id').select2({
    		data:data_info,
    		placeholder:"请您选择",
    		minimumInputLength:1,
    		maximumDisplayOptionsLength:5,
    		language:"zh-CN",width:"349px",
    		templateResult:myTemplateResult,templateSelection:myTemplateSelection
    		});
			
function myTemplateResult(res){
	if (res.loading) return res.text;
	res.id = res.id;
	if (isNotEmpty(res.code)) {
		return res.code + ":" + res.text;
	} else {return res.text;}
}

function myTemplateSelection(res){	
	return res.text;
}
//自定义 匹配规则，不仅匹配text还匹配code
function matchCustom(params, data) {
    // If there are no search terms, return all of the data
    if ($.trim(params.term) === '') {
      return data;
    }

    // Do not display the item if there is no 'text' property
    if (typeof data.text === 'undefined') {
      return null;
    }

    // `params.term` should be the term that is used for searching
    // `data.text` is the text that is displayed for the data object
    if (data.text.indexOf(params.term) > -1 || (data.hasOwnProperty('code') && data.code.indexOf(params.term) > -1)) {
      var modifiedData = $.extend({}, data, true);
      modifiedData.text += ' (matched)';

      // You can return modified objects from here
      // This includes matching the `children` how you want in nested data sets
      return modifiedData;
    }

    // Return `null` if the term should not be displayed
    return null;
}
</script>

```

# Modify By

JasonLi

#Origin Source
https://github.com/select2/select2
