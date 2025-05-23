# DPML记忆模式提示词框架最佳实践

> **TL;DR:** 本文档提供DPML记忆模式提示词框架的最佳实践指南，包括知识库设计、记忆类型选择、操作建议和具体示例。

## 💡 最佳实践

### 知识库设计

角色的先验知识库设计应考虑以下因素：

- **结构化程度**：
  - 高度结构化：适合专业领域知识，便于精确检索
  - 半结构化：适合通用知识，平衡灵活性和组织性
  - 低结构化：适合创意和启发性内容，保持关联灵活性

- **知识粒度**：
  - 宏观框架：定义领域整体认知结构
  - 中观原则：定义关键概念和方法论
  - 微观细节：定义具体事实和操作步骤

- **表达方式推荐**：
  - 领域地图：使用思维导图表达知识间的关系
  - 分类表格：使用表格整理分类知识
  - 核心原则：使用编号列表表达重要规则和原则

- **资源引用特性**：
  - 预加载原则：knowledge标签中的所有资源引用都会在角色初始化时加载
  - 内容与引用平衡：综合使用直接内容和资源引用
  - 分级引用：核心知识内联，扩展知识通过资源引用

### 记忆类型选择

协议实现可以根据需求采用不同的记忆类型分类方法，以下是基于认知心理学的常见分类：

1. **陈述性记忆(declarative)**：事实性知识，包括：
   - 语义记忆：通用事实，如"Python是编程语言"
   - 时态记忆：时间相关信息，如"上次会话在昨天"

2. **程序性记忆(procedural)**：过程和技能知识，如：
   - 操作步骤：如"解决环境配置问题的方法"
   - 行动模式：如"用户代码风格偏好"

3. **情景记忆(episodic)**：特定经历和场景，如：
   - 交互记录：如"用户之前遇到的报错"
   - 场景重建：如"项目开发历程"

不同类型记忆的选择建议：
- 存储事实性信息时，考虑使用陈述性记忆方式
- 存储方法和步骤时，考虑使用程序性记忆方式
- 存储具体交互经历时，考虑使用情景记忆方式

### 记忆操作使用建议

- **knowledge最佳实践**：
  - 将核心知识组织为分层结构
  - 使用可视化图表表达知识间的关系
  - 区分"确定性知识"和"启发性知识"
  - 避免过于琐碎的细节，保持适当抽象
  - 确保所有关键知识都在角色初始化时可用
  - 平衡内联内容和资源引用，内联核心概念，引用详细信息
  - 使用资源引用时考虑加载成本，避免引用过大的资源

- **evaluate最佳实践**：
  - 明确设定评估标准
  - 综合考虑信息的稀有性、实用性和时效性
  - 避免过度记忆导致的信息冗余

- **store最佳实践**：
  - 为记忆提供足够的上下文
  - 建立适当的记忆关联
  - 设置合理的过期策略

- **recall最佳实践**：
  - 设计清晰的记忆检索触发条件
  - 制定多层次的检索策略
  - 规划记忆应用的具体步骤
  - 处理记忆缺失的回退策略
  - 资源引用按需加载，注意引用路径的准确性

## 📋 使用示例

### 基础使用示例

```xml
<!-- 带知识库的简单记忆定义 -->
<memory id="tech_specialist">
  <knowledge>
    # 技术领域基础知识
    
    ## 核心概念（直接内联，预加载）
    - 编程语言：Python、JavaScript、Go
    - 开发框架：React、Django、Flask
    - 数据库技术：SQL、MongoDB、Redis
    
    ## 详细资料（资源引用，预加载）
    - @file://references/programming_languages.md
    - @file://references/frameworks.md
  </knowledge>

  <!-- 运行时记忆处理 -->
  <evaluate:thought>
    <reasoning>
      用户提供了特定的代码风格偏好，这对提供一致的代码建议很重要。
      评分：实用性=8，稳定性=9，总分8.5 > 阈值7.5
    </reasoning>
  </evaluate:thought>
  
  <store:execution>
    {
      "indent": "2spaces",
      "naming": "camelCase",
      "brackets": "sameLine"
    }
  </store:execution>
</memory>
```

### 高级使用示例

```xml
<!-- 完整的记忆生命周期示例 -->
<memory id="support_specialist">
  <!-- 知识库定义 -->
  <knowledge>
    # 技术支持专家知识库
    
    ```mermaid
    mindmap
      root((技术支持))
        常见问题
          依赖冲突
          环境配置
          性能优化
        诊断方法
          日志分析
          错误模式识别
          性能分析
        解决策略
          快速修复
          根本解决
          预防措施
    ```
    
    ## 优先级框架
    | 问题类型 | 优先级 | 响应时间 |
    |---------|-------|---------|
    | 系统宕机 | 紧急 | <30分钟 |
    | 功能障碍 | 高 | <2小时 |
    | 性能问题 | 中 | <1天 |
    | 功能建议 | 低 | <1周 |
    
    ## 知识库引用（全部预加载）
    - @file://kb/common_errors.md
    - @http://internal.docs/troubleshooting-guide.html
    - @db://support/solutions
  </knowledge>
  
  <!-- 评估阶段：判断是否值得记忆 -->
  <evaluate:thought>
    <reasoning>
      分析用户遇到的依赖安装错误:
      
      1. 问题特点:
         - 特定版本冲突问题
         - 解决方法非官方文档所列
         - 多次在社区中被报告
      
      2. 记忆价值:
         - 解决方案不易找到
         - 可能重复出现
         - 节省未来排查时间
      
      记忆价值评分：9/10，超过阈值
      决策：应当记忆此解决方案
    </reasoning>
  </evaluate:thought>
  
  <!-- 存储阶段：通过execution实现 -->
  <store:execution>
    问题：TensorFlow 2.4安装与CUDA 11.2版本冲突
    解决方案：使用兼容性补丁并降级CUDA驱动
    
    <!-- 使用execution协议元素定义存储过程 -->
    <process>
      # 存储流程
      
      ```mermaid
      flowchart TD
        A[接收内容] --> B[验证格式]
        B --> C[分类标记]
        C --> D[构建索引]
        D --> E[写入持久存储]
      ```
    </process>
    
    <rule>
      1. 解决方案记忆优先级设为高
      2. 建立与相关技术的关联索引
      3. 保存完整的上下文信息
    </rule>
  </store:execution>
  
  <!-- 检索阶段：通过thought实现 -->
  <recall:thought>
    <reasoning>
      根据当前用户描述的错误信息分析:
      - 涉及TensorFlow与CUDA版本问题
      - 错误模式与之前记录的类似
      - 应当检索相关解决方案
    </reasoning>
    
    <plan>
      # 记忆应用计划
      
      ```mermaid
      flowchart TD
        A[识别问题模式] --> B[检索相关记忆]
        B --> C[验证适用性]
        C -->|适用| D[应用解决方案]
        C -->|不适用| E[寻找替代方案]
        D --> F[监控结果]
      ```
      
      1. 检索TensorFlow相关解决方案
      2. 验证版本兼容性
      3. 提供定制化指导
      
      <!-- 按需加载的外部资源 -->
      @file://solutions/tensorflow_cuda_fixes.md
    </plan>
  </recall:thought>
</memory>
```

## 实现考虑事项

### 知识预加载与按需加载的平衡

- **预加载考虑**：knowledge标签中的所有内容和资源引用都预加载
  - 优点：对话开始时角色就拥有完整知识
  - 缺点：初始化成本高，特别是引用大型资源时
  
- **混合策略建议**：
  - 核心知识直接内联在knowledge标签中
  - 必要但不常用的知识通过资源引用方式组织
  - 极少使用的扩展知识放在recall中按需引用
  
- **性能优化**：
  - 对大型知识库考虑使用索引+按需加载模式
  - 使用分层加载策略：核心立即加载，细节延迟加载
  - 为循环引用建立保护机制，避免无限递归加载

> **注意**：memory协议现在包含四个核心组件：knowledge(先验知识库)、evaluate(评估)、store(存储)和recall(回忆)，共同构成完整的记忆系统。knowledge定义预加载知识，而其他组件负责运行时记忆管理。 