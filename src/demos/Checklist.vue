<template>
  <div>
    <checklist title="default checklist" :options="commonList" :value="checklist001" @on-change="change"></checklist>

    <checklist title="preselect China and Japan" :options="commonList" :value="checklist002" @on-change="change"></checklist>

    <checklist title="set max=2" :options="commonList" :value="checklist003" :max=2 @on-change="change"></checklist>

    <checklist title="set required=false and no min-error will show" :options="commonList" :value="checklist004" :max=2 :required=false @on-change="change"></checklist>

    <checklist title="set random order" random-order :options="checklist005" :value="checklist005Value" @on-change="change"></checklist>

    <checklist title="Option Array with key and value(key must be string)" :options="objectList" :value="objectListValue" @on-change="change"></checklist>

    <checklist title="Async list" :max="3" :options="asyncList" :value="asyncListValue" @on-change="change"></checklist>

    <divider>Reference</divider>
    <group title="See also">
      <cell title="Checker" value="with which you can custom any style" is-link link="/component/checker"></cell>
    </group>
  </div>
</template>

<script>
import { Group, Checklist, Cell, Divider } from '../components'

export default {
  mounted () {
    setTimeout(() => {
      this.asyncList = ['A', 'B', 'C', 'D']
    }, 3000)
  },
  components: {
    Group,
    Checklist,
    Cell,
    Divider
  },
  methods: {
    change (val) {
      console.log('change', val)
    }
  },
  data () {
    return {
      commonList: [ 'China', 'Japan', 'America' ],
      checklist001: [],
      checklist002: [ 'China', 'Japan' ],
      checklist003: [ 'China', 'Japan' ],
      checklist004: [],
      checklist005: [ '01', '02', '03' ],
      checklist005Value: [],
      objectList: [{key: '1', value: '001 value'}, {key: '2', value: '002 value'}, {key: '3', value: '003 value'}],
      objectListValue: ['1', '2'],
      asyncList: [],
      asyncListValue: []
    }
  }
}
</script>
