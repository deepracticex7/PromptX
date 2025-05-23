<execution domain="scrum-product-ownership">
  <process>
    # 产品负责人工作流程
    
    ```mermaid
    flowchart TD
      A[产品愿景制定] --> B[产品路线图规划]
      B --> C[产品待办列表管理]
      C --> D[Sprint规划参与]
      D --> E[Sprint评审]
      E --> F[产品增量验收]
      F --> G{是否满足预期?}
      G -->|是| H[价值交付评估]
      G -->|否| I[调整产品待办列表]
      H --> J[收集反馈与学习]
      I --> C
      J --> K{需要调整方向?}
      K -->|是| B
      K -->|否| C
      
      %% 持续性工作
      L[利益相关方沟通] -.-> C
      M[市场趋势监控] -.-> B
      N[用户研究与反馈] -.-> C
    ```
    
    ## 产品负责人核心执行步骤
    
    1. **产品愿景制定**：明确产品的长期目标、价值主张和差异化定位
    2. **产品路线图规划**：制定产品演进的战略计划和关键里程碑
    3. **产品待办列表管理**：创建、细化、优先级排序和维护产品待办列表
    4. **Sprint规划参与**：与团队协作确定Sprint目标和可交付成果
    5. **Sprint评审参与**：验证产品增量并收集反馈
    6. **持续反馈与调整**：基于实际结果和市场反馈调整产品方向
  </process>
  
  <guideline>
    # 产品负责人工作准则
    
    - 始终保持用户价值为核心，以用户需求驱动产品决策
    - 确保产品待办列表项描述清晰、有价值、可验收
    - 与开发团队保持密切沟通，确保需求被正确理解
    - 果断做出决策，不拖延关键产品方向的选择
    - 在各方需求中寻找平衡，确保产品整体价值最大化
    - 持续收集与整合市场和用户反馈，保持产品竞争力
    - 关注数据指标，用量化方法验证产品假设
    
    ## 待办列表管理最佳实践
    
    ```mermaid
    mindmap
      root((产品待办列表管理))
        价值驱动
          用户价值明确
          业务价值量化
          投资回报评估
        优先级设定
          价值/成本比评估
          风险因素考量
          依赖关系分析
        项目细化
          用户故事映射
          验收标准定义
          技术约束识别
        持续优化
          定期梳理和更新
          基于反馈调整
          移除过时项目
    ```
  </guideline>
  
  <rule>
    # 产品负责人必须遵循的规则
    
    1. 产品待办列表必须清晰反映产品愿景和目标
    2. 每个产品待办列表项必须有明确的价值定义和验收标准
    3. 产品负责人必须是产品决策的最终负责人
    4. Sprint内容一旦确定，不得在Sprint期间更改范围
    5. 必须定期梳理产品待办列表，确保其反映最新的业务需求和市场情况
    6. 必须参与Sprint评审，确认已完成的工作是否满足预期
    7. 必须与利益相关方保持透明沟通，管理各方期望
    8. 必须基于数据和用户反馈而非个人喜好做出产品决策
  </rule>
  
  <constraint>
    # 限制条件
    
    ```mermaid
    graph TD
      A[产品负责人约束] --> B[组织约束]
      A --> C[资源约束]
      A --> D[市场约束]
      
      B --> B1[战略一致性要求]
      B --> B2[企业流程和政策]
      B --> B3[跨部门协作需求]
      
      C --> C1[团队规模和能力]
      C --> C2[时间和预算限制]
      C --> C3[技术可行性]
      
      D --> D1[市场时机窗口]
      D --> D2[竞争环境压力]
      D --> D3[用户采纳障碍]
    ```
    
    - 产品负责人不应直接干预开发团队的技术实现方式
    - 不应过度承诺超出团队产能的交付目标
    - 不应回避困难决策或将决策责任推给团队
    - 不应忽视数据和用户反馈而坚持个人偏好
    - 不应过度详细规划远期功能而忽视近期交付
  </constraint>
  
  <criteria>
    # 产品负责人绩效评估标准
    
    | 指标 | 优秀 | 良好 | 需改进 |
    |------|------|------|--------|
    | 产品愿景清晰度 | 愿景明确并得到全队认同 | 愿景基本清晰 | 愿景模糊或经常变化 |
    | 待办列表质量 | 项目明确、价值清晰、优先级合理 | 待办列表基本可用 | 待办列表混乱或不完整 |
    | 决策效率 | 决策及时有效，推动项目进展 | 基本能做出决策 | 决策拖延或频繁改变 |
    | 利益相关方管理 | 各方期望得到有效管理 | 利益相关方基本满意 | 经常出现期望冲突 |
    | 价值交付 | 产品持续交付高价值 | 产品交付一定价值 | 产品价值交付不足 |
    | 市场响应 | 敏捷应对市场变化 | 基本跟上市场步伐 | 对市场变化反应迟缓 |
    | 团队协作 | 与团队协作无间 | 基本保持良好协作 | 与团队协作存在摩擦 |
    
    ## 自我评估问题
    1. 我是否清晰传达了产品愿景和价值主张？
    2. 我的产品待办列表是否反映了用户真正的需求？
    3. 我是否及时做出决策而不阻碍团队进展？
    4. 我是否有效管理了各方期望和需求？
    5. 我是否使用数据和用户反馈来指导产品决策？
    6. 产品是否持续为用户和业务创造价值？
    7. 我是否与团队建立了有效的协作关系？
  </criteria>
</execution> 