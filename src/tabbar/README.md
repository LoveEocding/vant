# Tabbar

### Install

```js
import Vue from 'vue';
import { Tabbar, TabbarItem } from 'vant';

Vue.use(Tabbar);
Vue.use(TabbarItem);
```

## Usage

### Basic Usage

```html
<van-tabbar v-model="active">
  <van-tabbar-item icon="home-o">Tab</van-tabbar-item>
  <van-tabbar-item icon="search">Tab</van-tabbar-item>
  <van-tabbar-item icon="friends-o">Tab</van-tabbar-item>
  <van-tabbar-item icon="setting-o">Tab</van-tabbar-item>
</van-tabbar>
```

```js
export default {
  data() {
    return {
      active: 0
    }
  }
}
```

### Match by name

```html
<van-tabbar v-model="active">
  <van-tabbar-item name="home" icon="home-o">Tab</van-tabbar-item>
  <van-tabbar-item name="search" icon="search">Tab</van-tabbar-item>
  <van-tabbar-item name="friends" icon="friends-o">Tab</van-tabbar-item>
  <van-tabbar-item name="setting" icon="setting-o">Tab</van-tabbar-item>
</van-tabbar>
```

```js
export default {
  data() {
    return {
      active: 'home'
    }
  }
}
```

### Show Badge

```html
<van-tabbar v-model="active">
  <van-tabbar-item icon="home-o">Tab</van-tabbar-item>
  <van-tabbar-item icon="search" dot>Tab</van-tabbar-item>
  <van-tabbar-item icon="friends-o" badge="5">Tab</van-tabbar-item>
  <van-tabbar-item icon="setting-o" badge="20">Tab</van-tabbar-item>
</van-tabbar>
```

### Custom Icon

Use `icon` slot to custom icon

```html
<van-tabbar v-model="active">
  <van-tabbar-item badge="3">
    <span>Custom</span>
      <template #icon="props">
        <img :src="props.active ? icon.active : icon.inactive"/>
      </template>
  </van-tabbar-item>
  <van-tabbar-item icon="search">Tab</van-tabbar-item>
  <van-tabbar-item icon="setting-o">Tab</van-tabbar-item>
</van-tabbar>
```

```js
export default {
  data() {
    return {
      active: 0,
      icon: {
        active: 'https://img.yzcdn.cn/vant/user-active.png',
        inactive: 'https://img.yzcdn.cn/vant/user-inactive.png'
      }
    }
  }
}
```

### Custom Color

```html
<van-tabbar
  v-model="active"
  active-color="#07c160"
  inactive-color="#000"
>
  <van-tabbar-item icon="home-o">Tab</van-tabbar-item>
  <van-tabbar-item icon="search">Tab</van-tabbar-item>
  <van-tabbar-item icon="freinds-o">Tab</van-tabbar-item>
  <van-tabbar-item icon="setting-o">Tab</van-tabbar-item>
</van-tabbar>
```


### Change Event

```html
<van-tabbar v-model="active" @change="onChange">
  <van-tabbar-item icon="home-o">Tab1</van-tabbar-item>
  <van-tabbar-item icon="search">Tab2</van-tabbar-item>
  <van-tabbar-item icon="freinds-o">Tab3</van-tabbar-item>
  <van-tabbar-item icon="setting-o">Tab4</van-tabbar-item>
</van-tabbar>
```

```js
import { Notify } from 'vant';

export default {
  methods: {
    onChange(index) {
      Notify({ type: 'primary', message: index });
    }
  }
}
```

### Route Mode

```html
<router-view />

<van-tabbar route>
  <van-tabbar-item replace to="/home" icon="home-o">
    Tab
  </van-tabbar-item>
  <van-tabbar-item replace to="/search" icon="search">
    Tab
  </van-tabbar-item>
</van-tabbar>
```

## API

### Tabbar Props

| Attribute | Description | Type | Default |
|------|------|------|------|
| v-model | Identifier of current tab | *number \| string* | `0` |
| fixed | Whether to fixed bottom | *boolean* | `true` |
| border | Whether to show border | *boolean* | `true` |
| z-index | Z-index | *number \| string* | `1` |
| active-color | Color of active tab item | *string* | `#1989fa` |
| inactive-color | Color of inactive tab item | *string* | `#7d7e80` |
| route | Whether to enable route mode | *boolean* | `false` |
| placeholder `v2.6.0` | Whether to generage a placeholder element when fixed | *boolean* | `false` |
| safe-area-inset-bottom | Whether to enable bottom safe area adaptation | *boolean* | `false` |

### Tabbar Events

| Event | Description | Arguments |
|------|------|------|
| change | Triggered when change active tab | active: index of current tab |

### TabbarItem Props

| Attribute | Description | Type | Default |
|------|------|------|------|
| name | Identifier | *number \| string* | Item index |
| icon | Icon name | *string* | - |
| icon-prefix `v2.5.3` | Icon className prefix | *string* | `van-icon` |
| dot | Whether to show red dot | *boolean* | - |
| badge `v2.5.6` | Content of the badge | *number \| string* | `''` |
| url | Link | *string* | - |
| to | Target route of the link, same as to of vue-router | *string \| object* | - |
| replace | If true, the navigation will not leave a history record | *boolean* | `false` |

### TabbarItem Slots

| Name | Description | SlotProps |
|------|------|------|
| icon | Custom icon | active |
