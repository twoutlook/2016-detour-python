#  take note of <b>Writing your first Django app, part 4</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial04/

## Write the first Form
- 在單一的問題頁面會出現預擬的選項，現在可以選擇提交。
- 提交後會進到看結果的頁面，顯示各選項的值，並可回到投票頁。
- 信息安全︰ race condition!!!
- view.py 啟用 class IndexView(generic.ListView):
