#  take note of <b>Writing your first Django app, part 5</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial05/

## 測試自動化
- What
- Why
  -- Save you time
  -- Prevent problem
  -- Make code attractive
  -- Help teams work together
  
- 信息安全︰ race condition!!!
- view.py 啟用 class IndexView(generic.ListView):

## 實做
- 發現沒有 import datetime 的問題
- 跟著範例自己加
```
    def test_123_a(self):
        val=123
        self.assertEqual(val==123, False)
    def test_123_b(self):
        val=123
        self.assertEqual(val,234)
    def test_123_c(self):
        val=123
        self.assertEqual(val,123)

```


