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
</script>

```

# Modify By

JasonLi

#Origin Source
https://github.com/select2/select2