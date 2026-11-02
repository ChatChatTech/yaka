# HiYaKa 固件公开快照

| 字段 | 当前值 |
|---|---|
| 发布日期 | 2026-11-02 |
| 私有开发来源 | `njueeRay/hi-yaka-firmware` |
| 来源提交 | `5838a1ea4c11307a58c49f8ba299ab9261773ca9` |
| 小智上游 | `78/xiaozhi-esp32` |
| 上游基线 | `v2.5.2` / `49b4380b3faa0ceadd28a3e78aaf0f311c46c57e` |
| ESP-IDF | 6.1 |
| GitHub 宿主 runner | `ubuntu-24.04` |
| 构建容器 | `espressif/idf:v6.1` |
| HiYaKa 板型 | `chatchat/hi-yaka` / `hi-yaka` |
| 当前阶段 | PH0–PH5 已关闭；M1 安全基线与 M2–M5 实板前适配完成，等待实板验证 |
| 最高证据等级 | L0 |
| 私有来源 CI | [产品核心](https://github.com/njueeRay/hi-yaka-firmware/actions/runs/41393072856) · [板型矩阵](https://github.com/njueeRay/hi-yaka-firmware/actions/runs/41393072860) · [板级合同](https://github.com/njueeRay/hi-yaka-firmware/actions/runs/41393072858) |

## 快照包含内容

- 可构建的固件源码、依赖声明、16 MiB 双 OTA 分区、HiYaKa 板型与构建脚本；
- M2–M5 的分模块安全开关，以及显示、输入、反馈、电池、音频、TF/FatFs 录音和产品运行时适配；
- LCD 使用 PARLIO、TF 独占 SPI2 的 ESP32-C6 资源合同，安全构建与实验构建严格分离；
- 产品状态协调、业务闭环、可靠录音合同、OTA/资源保障和宿主测试；
- 首板操作顺序、15 个模块记录模板、M1–M7/L0–L3 映射和不可覆盖证据工具；
- 固件 PRD 与里程碑、硬件连接与固件接口契约、固件架构、M1 基线和证据规则；
- 上游 MIT 许可证、原始版权声明和 ChatChatTech 对新增/修改内容的版权声明。

## 未公开内容

- 私有仓库 Git 历史和开发分支；
- 项目 Agent/Skill、内部操作指令、远程环境和凭据信息；
- 飞书 token、同步登记、产品决策台账与内部工作手册；
- 原理图/PCB/SMT/采购审计及供应链执行文件；
- 未经发布评审的实板日志、缺陷和产品决策。

## 当前验证结论

私有来源在固定 Ubuntu 24.04 GitHub runner 和 ESP-IDF 6.1 容器中通过安全构建、实验构建、宿主合同、板级合同、资源门禁、21 项定向测试和 20 个构建变体。应用镜像为 1,930,544 字节，占门禁上限 49.93%；内部 DIRAM 使用 126,429/452,112 字节（27.96%）。正式 `main` 合并镜像 SHA-256 为 `ecd404a7d3bc0492d44612ed68e2638425a6237af8805234516a2c401335064e`。公开仓库另设独立流水线，从 `firmware/` 快照重新执行同类门禁。

上述结论只属于 L0 软件证据，不证明 Flash、I²C 地址、安全电平、显示、音频、TF、NFC、IMU、电源或 OTA 已经通过真实样机验证。M1 及全部实板能力仍无 L1/L2/L3 结论，因此本次更新不是面向终端用户的产品 Release。

## 更新规则

公开快照通过独立 PR 更新。每次更新必须修改本文件中的来源提交和验证结论，重新运行公开 CI，并检查公开差异、凭据、许可证和内部资料泄露。禁止把私有仓库直接设置为本目录的 subtree 或镜像来源。
