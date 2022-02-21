<template>
  <div class="el-table flex-1">
    <table class="table">
      <thead>
        <tr>
          <th
            v-for="(header, index) in headers"
            :key="index"
            :width="header.width"
          >
            <div class="flex-center">
              <span>{{ header.text }}</span>
            </div>
          </th>
        </tr>
      </thead>
      <tbody v-if="items.length">
        <tr
          v-for="item in items"
          :key="item.id"
          @click.prevent="openUser(item)"
        >
          <td v-for="(header, index) in headers" :key="index">
            <span>{{ item[header.field] }}</span>
          </td>
        </tr>
      </tbody>
      <tbody v-else><tr><td style="font-size: 14px;">Данные отсутствуют</td></tr></tbody>
    </table>
  </div>

</template>

<script>
export default {
  name: 'ElTable',
  props: {
    items: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      headers: [
        { field: 'name', text: 'Фамилия имя', width: '25%' },
        { field: 'email', text: 'email', width: '25%' },
        { field: 'website', text: 'Сайт', width: '25%' },
        { field: 'phone', text: 'телефон', width: '25%' }
      ]
    }
  },
  methods: {
    openUser(user) {
      this.$router.push({path: '/users/' + user.id, query: { name: user.name}})
    }
  }
}
</script>

<style lang="scss">
.el-table {
  box-sizing: border-box;

  table {
    border-spacing: 0;
    min-width: 100%;
    background: #fff;
    font-size: 16px;
    line-height: 22px;

    thead {
      font-weight: bold;

      tr th {
        color: rgb(144, 147, 153);
        position: relative;
        vertical-align: center;
        text-align: left;
        border-bottom: 1px solid #ebedf2;
      }
    }

    tbody {
      border-top: none;

      tr td {
        height: 30px;
        font-size: 16px;
        line-height: 16px;
        position: relative;
        text-overflow: ellipsis;
        overflow: hidden;
        color: rgb(96, 98, 102);
        border-bottom: 1px solid rgba(235, 237, 242, 0.6);
      }

      tr:hover {
        background-color: #f5f7fa;
      }
    }
  }
}

.table {
  width: 100%;
  border-collapse: collapse;

  th, td {
    padding: 10px 15px;
    text-align: left;
  }
}

.flex {
  display: flex;

  &-1 {
    flex: 1;
    display: flex;
  }

  &-column {
    display: flex;
    flex-direction: column;
  }

  &-center {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &-left {
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
  }
}
</style>
