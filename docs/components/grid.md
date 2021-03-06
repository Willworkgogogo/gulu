---
sidebarDepth: 0
---

# Grid 栅格

24 栅格系统。

## 代码演示

### 基础栅格

从堆叠到水平排列。
使用单一的一组 Row 和 Col 栅格组件，就可以创建一个基本的栅格系统，所有列（Col）必须放在 Row 内。

<ClientOnly>
  <grid-basic />
</ClientOnly>

```vue
<template>
	<div>
		<w-row gutter="16">
			<w-col span="12">col-12</w-col>
			<w-col span="12">col-12</w-col>
		</w-row>
		<w-row gutter="16">
			<w-col span="8">col-8</w-col>
			<w-col span="8">col-8</w-col>
			<w-col span="8">col-8</w-col>
		</w-row>
		<w-row gutter="16">
			<w-col span="6">col-6</w-col>
			<w-col span="6">col-6</w-col>
			<w-col span="6">col-6</w-col>
			<w-col span="6">col-6</w-col>
		</w-row>
	</div>
</template>
```

### 区块间隔

栅格常常需要和间隔进行配合，你可以使用 Row 的 gutter 属性。

<ClientOnly>
  <grid-gutter />
</ClientOnly>

```vue
<template>
	<div>
		<w-row gutter="8">
			<w-col span="12">col-12</w-col>
			<w-col span="12">col-12</w-col>
		</w-row>
		<w-row gutter="16">
			<w-col span="8">col-8</w-col>
			<w-col span="8">col-8</w-col>
			<w-col span="8">col-8</w-col>
		</w-row>
		<w-row gutter="32">
			<w-col span="6">col-6</w-col>
			<w-col span="6">col-6</w-col>
			<w-col span="6">col-6</w-col>
			<w-col span="6">col-6</w-col>
		</w-row>
	</div>
</template>
```

### 左右偏移

列偏移。

使用 offset 可以将列向右侧偏。例如，offset="4" 将元素向右侧偏移了 4 个列（column）的宽度。

<ClientOnly>
  <grid-offset />
</ClientOnly>

```vue
<template>
	<div class="demo">
		<w-row>
			<w-col span="8">col-8</w-col>
			<w-col span="8" offset="8">col-8 col-offset-8</w-col>
		</w-row>
		<w-row>
			<w-col span="6" offset="6">col-6 col-offset-6</w-col>
			<w-col span="6" offset="6">col-6 col-offset-6</w-col>
		</w-row>
		<w-row>
			<w-col span="12" offset="6">col-12 col-offset-6</w-col>
		</w-row>
	</div>
</template>
```

## Flex 对齐

Flex 子元素垂直对齐。

<ClientOnly>
  <grid-flex />
</ClientOnly>

```vue
<template>
	<div class="demo">
		<p class="title">Align Top</p>
		<w-row justify="center" align="top">
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
		</w-row>
		<p class="title">Align Center</p>
		<w-row justify="space-around" align="center">
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
		</w-row>
		<p class="title">Align Bottom</p>
		<w-row justify="space-between" align="bottom">
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
			<w-col span="4">
				<span>col-4</span>
			</w-col>
		</w-row>
	</div>
</template>
```

## 响应式

参照 Bootstrap 的 [响应式设计](https://getbootstrap.com/docs/3.4/css/)，预设六个响应尺寸：`xs` `sm` `md` `lg` `xl` `xxl`。

<ClientOnly>
  <grid-bootstrap />
</ClientOnly>

```vue
<w-row>
	<w-col :xs="{span:24}" :sm="{span:4}" :md="{span:6}" :lg="{span: 8}" :xl="{span:10}"></w-col>
	<w-col :xs="{span:24}" :sm="{span:16}" :md="{span:12}" :lg="{span: 8}" :xl="{span:4}"></w-col>
	<w-col :xs="{span:24}" :sm="{span:4}" :md="{span:6}" :lg="{span: 8}" :xl="{span:10}"></w-col>
</w-row>
```

## API

### WRow

| 属性    | 说明                                                                             | 类型          | 默认值 |
| ------- | -------------------------------------------------------------------------------- | ------------- | ------ |
| gutter  | 栅格间隔                                                                         | string/number | -      |
| align   | flex 布局下的垂直对齐方式：`top` `middle` `bottom`                               | string        | top    |
| justify | flex 布局下的水平排列方式：`start` `end` `center` `space-around` `space-between` | string        | start  |

### WCol

| 属性   | 说明                                         | 类型          | 默认值 |
| ------ | -------------------------------------------- | ------------- | ------ |
| span   | 栅格占位格数，为 0 时相当于 display: none    | string/number | -      |
| offset | 栅格左侧的间隔格数，间隔内不可以有栅格       | string/number | 0      |
| xs     | `<576px` 响应式栅格，一个包含其他属性的对象  | object        | -      |
| sm     | `≥576px` 响应式栅格，一个包含其他属性的对象  | object        | -      |
| md     | `≥768px` 响应式栅格，一个包含其他属性的对象  | object        | -      |
| lg     | `≥992px` 响应式栅格，一个包含其他属性的对象  | object        | -      |
| xl     | `≥1200px` 响应式栅格，一个包含其他属性的对象 | object        | -      |
| xxl    | `≥1600px` 响应式栅格，一个包含其他属性的对象 | object        | -      |
