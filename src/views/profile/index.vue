<template>
  <div v-if="user" style="padding: 10px 10px 50px 10px">
    <el-row :gutter="10">
      <el-col :span="8" :xs="24">
        <user-card :user="user" />
      </el-col>
      <el-col :span="16" :xs="24">
        <el-card>
          <el-tabs v-model="activeTab">
            <el-tab-pane :label="$t('common.timeline')" name="timeline">
              <timeline />
            </el-tab-pane>
            <el-tab-pane :label="$t('common.account')" name="account">
              <account :user="user" />
            </el-tab-pane>
            <el-tab-pane :label="$t('common.password')" name="password">
              <password />
            </el-tab-pane>
          </el-tabs>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import UserCard from './components/UserCard'
import Password from './components/Password'
import Timeline from './components/Timeline'
import Account from './components/Account'

export default {
  name: 'Profile',
  components: { UserCard, Password, Timeline, Account },
  data() {
    return {
      activeTab: ''
    }
  },
  computed: {
    user() {
      return this.$store.state.account.user
    }
  },
  created() {
    this.activeTab = 'timeline'
  }
}
</script>
<style lang="scss" scoped>
.el-card.is-always-shadow {
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
}

.el-card {
  border: none;
  border-radius: 0;
}
</style>
<style lang="scss">
.el-card__body {
  padding: 20px;
}
</style>
