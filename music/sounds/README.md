# 音色文件放这里

播放器会从这个目录读取 `<音色名>.ogg`。**缺哪个就用合成音代替**，不影响播放。

## 需要的文件

| 文件名 | 对应 | 用途 |
|---|---|---|
| `harp.ogg` | 钢琴/竖琴 | G 块默认（高音） |
| `bass.ogg` | 贝斯 | F 块默认（低音） |
| `guitar.ogg` | 吉他 | 标签 `G(guitar):` |
| `flute.ogg` | 长笛 | 标签 `G(flute):` |
| `chime.ogg` | 风铃 | 标签 `G(chime):` |
| `basedrum.ogg` | 底鼓 | 鼓 200 / 203 / 204 |
| `snare.ogg` | 军鼓 | 鼓 201 / 202 |
| `hat.ogg` | 踩镲 | 鼓 205 / 206 / 207 / 208 |

可选的还有 `bell.ogg`、`xylophone.ogg`（预留，暂时用不到）。

## 从自己的客户端提取

这些音频在客户端资源里：

```
.minecraft/assets/objects/<hash 目录>/...     ← 需要按索引文件查 hash
```

更简单的办法：用压缩软件打开 `客户端.jar` 或资源包，路径是

```
assets/minecraft/sounds/block/note_block/
    harp.ogg  basedrum.ogg  snare.ogg  hat.ogg  bass.ogg
    bell.ogg  flute.ogg  chime.ogg  guitar.ogg  xylophone.ogg
    iron_xylophone.ogg  cow_bell.ogg  didgeridoo.ogg  bit.ogg
    banjo.ogg  pling.ogg
```

把这些 `.ogg` 直接复制到这里，**改名为上表的名字**（大部分原名就对）。

## 版权提醒

Minecraft 音效受版权保护。**公开仓库不建议放这些文件**：

| 用途 | 建议 |
|---|---|
| 自己听 / 小范围分享 | 放进去没问题 |
| 公开 GitHub 仓库 | 只放 `.txt` 乐谱，音频自己本地放（或加进 `.gitignore`） |

`.gitignore` 示例：

```
music/sounds/*.ogg
```

## 音高说明

游戏里的音符盒是"同一个采样 + 变调播放"：

```
playbackRate = 2 ^ ((音高 - 采样基准) / 12)
```

五种乐器的采样基准（和游戏一致）：

| 乐器 | 基准 MIDI |
|---|---|
| harp | 54 |
| bass | 42 |
| guitar | 54 |
| flute | 66 |
| chime | 78 |

所以同一个音在不同乐器上会用不同的变调比例，和游戏里听到的一致。
