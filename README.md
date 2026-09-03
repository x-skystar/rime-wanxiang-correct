# 基于万象拼音 PRO 的双拼纠错扩展

支持**自然码双拼**和**小鹤双拼**。

---

## 📥 资源下载

请前往 [📦 Releases 页面](https://github.com/x-skystar/rime-wanxiang-correct/releases/tag/v1.0.0) 下载对应双拼方案的扩展包：

- **自然码双拼**：`zrm_correct.zip`
- **小鹤双拼**：`flypy_correct.zip`

---

## 🛠️ 安装教程

### 🔹 自然码双拼用户

1. 下载 `zrm_correct.zip` 安装包；
2. 解压后，把里面的文件放入 Rime 用户目录下的 `lua/wanxiang` 文件夹中；
3. 在 Rime 用户目录中找到或新建 `wanxiang_pro.custom.yaml` 文件，在末尾追加以下配置：

```yaml
patch:
  engine/translators/+:
    - lua_translator@*wanxiang.zrm_correct
  engine/filters/+:
    - lua_filter@*wanxiang.zrm_correct*F
  zrm_correction:
    enable: true
    beam: 15
    quality: 100
    strong_delta: 3.0
    topk: 2
    topk_seq: 3
    topk_legal: 2
    margin: 0.5
    margin_slope: 0.1
    weak_quality: 2
    w_learn: 30.0
    max_syllables: 15
```

4. 重新部署。

---

### 🔹 小鹤双拼用户

1. 下载 `flypy_correct.zip` 安装包；
2. 解压后，把里面的文件放入 Rime 用户目录下的 `lua/wanxiang` 文件夹中；
3. 在 Rime 用户目录中找到或新建 `wanxiang_pro.custom.yaml` 文件，在末尾追加以下配置：

```yaml
patch:
  engine/translators/+:
    - lua_translator@*wanxiang.flypy_correct
  engine/filters/+:
    - lua_filter@*wanxiang.flypy_correct*F
  zrm_correction:
    enable: true
    beam: 15
    quality: 100
    strong_delta: 3.0
    topk: 2
    topk_seq: 3
    topk_legal: 2
    margin: 0.5
    margin_slope: 0.1
    weak_quality: 2
    w_learn: 30.0
    max_syllables: 15
```

4. 重新部署。

---

## 🗑️ 卸载方法

1. 删除 `lua/wanxiang` 目录里添加的纠错扩展文件；
2. 删除 `lua/wanxiang` 目录里生成的 `zrm_learn.bin` 文件；
3. 删除在 `wanxiang_pro.custom.yaml` 文件中追加的补丁配置；
4. 重新部署输入法即可。
