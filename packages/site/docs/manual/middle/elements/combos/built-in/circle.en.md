---
title: Circle
order: 1
---

Built-in Circle Combo has the default style as below, the label is drawed on the center of it. <a href='/en/examples/item/defaultCombos#circle' target='_blank'>Demo</a> <br /> <img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*ijeuQoiH0JUAAAAAAAAAAABkARQnAQ' width=150 alt='img'/>

## Usage

As stated in [Built-in Combos](/en/docs/manual/middle/elements/combos/default-combo) , there are three methods to configure combos: Configure combos globally when instantiating a Graph; Configure combos in their data; Configure combos by `graph.combo(comboFn)`. Their priorities are:

`graph.combo(comboFn` > Configure in data > Configure globally

<span style="background-color: rgb(251, 233, 231); color: rgb(139, 53, 56)"><strong>⚠️ Attention:</strong></span> Expect for `id`, `parentId`, and `label` which should be assigned to every single combo data, the other configurations in [The Common Property](/en/docs/manual/middle/elements/combos/default-combo#common-property) and in each combo type (refer to doc of each combo type) support to be assigned by the three ways.

<span style="background-color: rgb(251, 233, 231); color: rgb(139, 53, 56)"><strong>⚠️ Attention:</strong></span> Must set the `groupByTypes` to `false` when instantiating the graph, which will result in rendering result with reasonable visual zIndex for combos.

### 1 Global Configure When Instantiating a Graph

Assign `type` to `'circle'` in the `defaultCombo` object when instantiating a Graph:

```javascript
const graph = new G6.Graph({
  container: 'mountNode',
  width: 800,
  height: 600,
  // Set groupByTypes to false to get rendering result with reasonable visual zIndex for combos
  groupByTypes: false,
  defaultCombo: {
    type: 'circle', // The type of the combo
    // ... Other configuraltions
  },
});
```

### 2 Configure in the Data

To configure different combo with different properties, you can write the properties into the combo data.

```javascript
const data = {
  nodes: [
    ... // nodes
  ],
  edges: [
    ... // edges
  ],
  combos: [
    {
      id: 'combo1',
      type: 'circle', // The tyep of the combo
      ... // Other configurations
    },
    ... // Other combos
  ]
};
```

## Property

The [Combo Common Properties](/en/docs/manual/middle/elements/combos/default-combo/#common-property) are available for Circle combo, some special properties are shown below. The property with Object type will be described after the table:<br />

| Name | Description | Type | Remark |
| --- | --- | --- | --- |
| size | The MINIMUM diameter of the combo (not for fixing the size) | number / number[] | When it is an array, the first element will take effect |
| fixSize | Fix the size of the combo | number | If it is not assigned, the rendering size of the combo depends on the sizes and distribution of its children items. If the `fixSize` is assigned but the `fixCollapseSize` is not, the size of the collapsed combo will still be `fixSize` |
| fixCollapseSize | Fix the size of the collapsed combo | number | If it is not assigned and the `fixSize` is assigned, the size of the collapsed Combo is `fixSize`; and if `fixCollapseSize` and `fixSize` are both not assigned, the size of the collapsed Combo is `size` ｜ |
| style | The default style of circle combo | Object | Refer to the [style](#style) |
| label | The text of the label | String |  |
| labelCfg | The configurations of the label | Object | Refer to the [labelCfg](#labelcfg) |
| stateStyles | The styles in different states | Object | Refer to [Configure Styles for State](/en/docs/manual/middle/states/state#configure-styles-for-state) |

### style

The [Combo Common Styles](/en/docs/manual/middle/elements/nodes/default-node/#style) are available for Circle combo. `style` is an object to configure the filling color, stroke, and other styles. The following code shows how to configure the `style` globally when instantiating a Graph.<br /> <img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*ydTKSqv-lh4AAAAAAAAAAABkARQnAQ' width=150 alt='img'/>

```javascript
const data = {
  combos: [
    {
      label: 'combo_circle',
      type: 'circle',
      label: 'Circle',
    },
  ],
};
const graph = new G6.Graph({
  container: 'mountNode',
  width: 800,
  height: 600,
  // Set groupByTypes to false to get rendering result with reasonable visual zIndex for combos
  groupByTypes: false,
  defaultCombo: {
    // type: 'circle',  // The type has been assigned in the data, we do not have to define it any more
    style: {
      fill: '#bae637',
      stroke: '#eaff8f',
      lineWidth: 5,
    },
  },
});
graph.data(data);
graph.render();
```

### labelCfg

`labelCfg` is an object to configure the label of the combo. The [Combo Common Label Configurations](/en/docs/manual/middle/elements/combos/default-combo/#label-and-labelcfg) are available. Base on the code in [style](#style) section, we add `labelCfg` to `defaultCombo`.<br /><img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*oQnLQZ__8K0AAAAAAAAAAABkARQnAQ' width=150 alt='img'/>

```javascript
const data = {
  // ... data
};
const graph = new G6.Graph({
  // ... Other configurations for graph
  // Set groupByTypes to false to get rendering result with reasonable visual zIndex for combos
  groupByTypes: false,
  defaultCombo: {
    // ... Other properties for combos
    labelCfg: {
      position: 'bottom',
      refX: 5,
      style: {
        fill: '#bae637',
        fontSize: 15,
        // ... The style of the label
      },
    },
  },
});
// ...
```
