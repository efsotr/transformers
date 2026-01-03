结论：当 `num_beams=4` 且未开启采样（`do_sample=False`，默认）时，`top_k` 参数不会生效；只有开启采样（例如 beam sampling：`num_beams>1` 且 `do_sample=True`）时 `top_k` 才会起作用，此时设置 `top_k=1` 等价于每个 beam 都按贪心选择，不增加随机性。

Conclusion: With `num_beams=4`, `top_k` is ignored when sampling is off (`do_sample=False`, default). It only matters during sampling (e.g., beam sampling with `num_beams>1` and `do_sample=True`), where `top_k=1` makes each beam pick greedily without adding randomness.
