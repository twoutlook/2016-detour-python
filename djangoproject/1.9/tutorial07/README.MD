#  take note of <b>Writing your first Django app, part 7</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial07/

## Customize admin form

- Register Question 可以客製欄位順序、分組。
- 答案組可以隨著問題一起編輯，子表格可以是表格式顯示。
- 問題列表可以調整要顯示的欄位，欄位標題可以是中文。
- 篩選，一開始沒有做成功。
  - 原來是應該在 class QuestionAdmin(admin.ModelAdmin):
- 查找，文字式, 要指定欄位的。


```
  C:\2016-djangoproject\mysite>python -c "import django; print(django.__path__)"
['D:\\Python\\Python35-32\\lib\\site-packages\\django']
```

D:\Python\Python35-32\Lib\site-packages\django\contrib\admin\templates\admin\base_site.html

- 最後一段教在 root 新建 templates\admin 並複製修改 base_site.html
  -  有點做錯，但更正過來了 
