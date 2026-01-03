<!--Copyright 2022 The HuggingFace Team. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with
the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.

⚠️ Note that this file is in Markdown but contain specific syntax for our doc-builder (similar to MDX) that may not be
rendered properly in your Markdown viewer.

-->

# Generation

每个框架都在它们各自的 `GenerationMixin` 类中实现了文本生成的 `generate` 方法：

- PyTorch [`~generation.GenerationMixin.generate`] 在 [`~generation.GenerationMixin`] 中实现。

无论您选择哪个框架，都可以使用 [`~generation.GenerationConfig`] 类实例对 generate 方法进行参数化。有关生成方法的控制参数的完整列表，请参阅此类。

> [!INFO]
> - `pipeline("text-generation")` 会在实例化时以管道的 `_default_generation_config`（`max_new_tokens=256`、`do_sample=True`、`temperature=0.7`）为基底，并调用 `model._prepare_generation_config` 合并配置，优先级为：调用时显式传入的生成参数（或 `generation_config`） > 模型仓库中的 `generation_config.json`（不存在时退回 `config.json` 推断出的生成参数） > 管道默认值。
> - 直接调用 `model.generate()` 时，`GenerationMixin._prepare_generation_config` 以“显式传入的 `generation_config`/`**kwargs` > `model.generation_config`（加载自 `generation_config.json`，若不存在则由 `config.json` 推断） > 全局默认生成配置”的顺序得到最终的生成配置。

要了解如何检查模型的生成配置、默认值是什么、如何临时更改参数以及如何创建和保存自定义生成配置，请参阅 [文本生成策略指南](../generation_strategies)。该指南还解释了如何使用相关功能，如token流。

## GenerationConfig

[[autodoc]] generation.GenerationConfig
	- from_pretrained
	- from_model_config
	- save_pretrained

## GenerationMixin

[[autodoc]] generation.GenerationMixin
	- generate
	- compute_transition_scores
