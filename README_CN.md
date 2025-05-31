# Coin-Meme

该数据集为论文 **《连接文化与金融：Web3 生态系统中模因币的多模态分析》**（将在 ACM The Web Conference (WWW'25) 发表）所使用的官方数据集。论文可在[此处](data/coin_meme.pdf)获取。

---

## 数据集概览

Coin-Meme 数据集包含 **3,751 种模因币**，这些模因币创建于 2024 年 1 月至 2024 年 11 月，并最终迁移至 Raydium。数据集提供了模因币生态系统的四种模态信息：

![数据集概览](https://github.com/user-attachments/assets/480e9948-8feb-45d3-95ce-adcba586a4f6)

---

## 数据模态

### 1. 文本描述
- **内容**：与每种模因币相关的叙述信息。
- **示例**：项目目标、文化参考、社区驱动的故事等。

### 2. 视觉内容
- **内容**：模因币的标志（Logo）图像。
- **规格**：存储为 RGB 图像，以保证一致性。

### 3. 社区互动
- **内容**：用户评论，反映社区参与情况。
- **来源**：从 Pump.fun 的代币专属页面提取。

### 4. 金融数据
- **指标**：  
  - **市值（Market Capitalization）**：代币估值。  
  - **市场进入时间（Market Entry Time）**：从代币发行到流动性迁移至 Raydium 的时间间隔。

---

## 数据获取

### 数据处理流程

1. **元数据提取**：
   - 来源：通过 `Dune.com` 获取 Pump.fun 相关数据（`6EF8rrecthR5Dkzon8Nwu78hRvfCKubJ14M5uBEwF6P`）。
   - 字段：代币地址、创建时间、名称、创建者等。

2. **网页爬取**：
   - 工具：Selenium + Pandas（数据处理）。
   - URL 生成：通过代币地址拼接 `https://pump.fun/` 形成访问链接。
   - 提取数据：描述信息、图像、评论、金融指标。

---

## 数据清理

### 文本数据
- 统一小写，去除非字母字符和 URL。
- 停用词去除、分词、词形还原。
- 剔除缺失文本的条目。

### 图像数据
- 调整大小至 **224x224 像素**（兼容 ResNet50）。
- 非 RGB 图像转换为 RGB 格式。
- 损坏或缺失的图像替换为零向量。

### 金融数据
- **市场进入时间**：计算方式为代币发行时间与迁移至 Raydium 的时间差。

---

## 参考文献

如果您使用此数据集，请引用我们的论文：

```bibtex
@inproceedings{long2025bridging,
  title={Bridging Culture and Finance: A Multimodal Analysis of Memecoins in the Web3 Ecosystem},
  author={Long, Hou-Wan and Wong, Nga-Man and Cai, Wei},
  booktitle={Companion Proceedings of the ACM on Web Conference 2025},
  pages={1158--1161},
  year={2025}
}
