# MutationObserver 监控DOM

## 简述

  在DOM结构被修改时执行异步回调. 使用MutationObserver接口可以关泽整个文档、DOM数的一部分或某个元素,元素属性、子节点、文本或者前三者任意组合的变化。

## 特性

- 关联到DOM时必须有属性是true  否则会报错

- 带有oldValue的属性的开启会将该项的检测属性改为true

- 若记录旧的数据 则MutationObserver的回调函数将接受所有的历史变化recordArr

- 排序等操作会响应两次

- DOM被卸载则监测行为也会被清理

## 起步API

- 创建

      let observer = new MutationObserver((recordArr) => console.log('DOM was mutated!'));

- 关联到DOM

      config = {
        attributes: true, // 是否检测目标的属性变化
        childList: true, // 子节点数量列表
        subtree: true, // 是否监测目标的子树变化
        attributeFilter: [] || '', //需要监测目标的属性 值为数组或者字符串
        attributeOldValue: true, // 是否记录变化之前的属性值
        characterData: true, // 是否检测修改字符串数据
        characterDataOldValue,
        childList:  true // 是否监测目标的子节点

      };

      observer.observe(DOM, config);

- 结束

      observer.disconnect();
