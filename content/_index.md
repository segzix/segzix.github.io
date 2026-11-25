---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2026-01-05
type: landing

sections:
  # Developer Hero
  - block: dev-hero
    id: hero
    content:
      username: me
      greeting: "你好，我是"
      show_status: true
      show_scroll_indicator: true
      typewriter:
        enable: true
        prefix: "我在做"
        strings:
          - "LLM 推理系统优化"
          - "AI 芯片性能建模"
          - "高性能通信 (RDMA)"
        type_speed: 70
        delete_speed: 40
        pause_time: 2500
      cta_buttons:
        - text: 查看项目
          url: "#projects"
          icon: arrow-down
        - text: 联系我
          url: "#contact"
          icon: envelope
    design:
      style: centered
      avatar_shape: circle
      animations: true
      background:
        color:
          light: "#fafafa"
          dark: "#0a0a0f"
      spacing:
        padding: ["6rem", "0", "4rem", "0"]

  # Portfolio
  - block: portfolio
    id: projects
    content:
      title: "项目"
      subtitle: "我的部分工作"
      count: 0
      filters:
        folders:
          - projects
      buttons:
        - name: 全部
          tag: '*'
      default_button_index: 0
    design:
      columns: 3
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Tech Stack
  - block: tech-stack
    id: skills
    content:
      title: "技术能力"
      subtitle: "我常用的技术栈"
      categories:
        - name: 编程语言
          items:
            - name: C/C++
              icon: devicon/cplusplus
            - name: Python
              icon: devicon/python
        - name: 训推系统
          items:
            - name: vLLM
              icon: devicon/pytorch
            - name: PyTorch / FSDP
              icon: devicon/pytorch
        - name: 高性能计算
          items:
            - name: CUDA
              icon: devicon/nvidia
            - name: RDMA
              icon: devicon/linux
        - name: 系统 / 工具
          items:
            - name: Linux
              icon: devicon/linux
            - name: Git
              icon: devicon/git
            - name: Docker
              icon: devicon/docker
    design:
      style: grid
      show_levels: false
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Experience Timeline
  - block: resume-experience
    id: experience
    content:
      title: 经历
      date_format: 2006.01
      items:
        - title: 系统软件实习生（LLM 推理优化方向）
          company: 摩尔线程
          company_url: ''
          company_logo: ''
          location: 北京
          date_start: '2026-01-01'
          date_end: '2026-05-31'
          description: |2-
            * 面向大模型长上下文推理的 KV Cache 跨实例复用与快照恢复
            * 基于 RDMA 异步传输 + 后台快照 + userfaultfd 按需恢复
            * Prefill 开销降低约 65%，重启后首次命中 64s → 0.94s
        - title: AI 系统实习生（RL 后训练性能优化方向）
          company: 移动九天 AI
          company_url: ''
          company_logo: ''
          location: 北京
          date_start: '2026-06-01'
          date_end: '2026-09-30'
          description: |2-
            * 昇腾 NPU 上异步 RL 后训练（Qwen3-8B, vLLM）性能剖析与优化
            * 异步训练 + 训推卡数配比调整 + 推测解码
            * 单步耗时 1000s → 355s，吞吐最高 3.72×
    design:
      columns: '1'
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # Contact Section
  - block: contact-info
    id: contact
    content:
      title: 联系我
      subtitle: "欢迎交流 AI Infra / AI 芯片相关机会"
      text: |-
        我对AI Infra、AI 芯片的实习和工作很感兴趣。
        欢迎通过邮件联系我。
      email: shengzixuan.work@foxmail.com
      autolink: true
    design:
      columns: '1'
      background:
        color:
          light: "#ffffff"
          dark: "#0d0d12"
      spacing:
        padding: ["4rem", "0", "4rem", "0"]

  # CTA Card
  - block: cta-card
    content:
      title: "正在寻找机会"
      text: |-
        目前正在寻找 **AI Infra / AI 芯片** 方向的实习与全职机会。
        欢迎联系我进一步沟通。
      button:
        text: '下载简历'
        url: uploads/resume.pdf
        new_tab: true
    design:
      card:
        css_class: 'bg-gradient-to-br from-primary-200 via-primary-100 to-secondary-200 dark:from-primary-600 dark:via-primary-700 dark:to-secondary-700'
        text_color: dark
      background:
        color:
          light: "#f5f5f5"
          dark: "#08080c"
      spacing:
        padding: ["4rem", "0", "6rem", "0"]
---
