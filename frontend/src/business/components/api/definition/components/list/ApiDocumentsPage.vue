<template>
  <div>
    <api-document-anchor :is-share-page="isSharePage" :trash-enable="trashEnable"
                         :module-ids="moduleIds" :project-id="projectId" :version-id="versionId"
                         ref="documentAnchor"/>
  </div>
</template>

<script>

import ApiDocumentAnchor from "@/business/components/api/definition/components/document/ApiDocumentAnchor";

export default {
  name: "ApiDocumentsPage",
  components: {
    ApiDocumentAnchor
  },
  data() {
    return {
      isSharePage: false,
      condition: {},
    };
  },
  props: {
    projectId: String,
    moduleIds: Array,
    versionId: String,
    activeDom: String,
    trashEnable: {
      type: Boolean,
      default: false,
    },
  },
  created: function () {
  },
  watch: {
    versionId() {
      this.initApiDocSimpleList();
    }
  },
  computed: {},
  methods: {
    initApiDocSimpleList() {
      this.condition.versionId = this.versionId;
      Object.assign(this.$refs.documentAnchor.apiSearch, this.condition);
      this.$refs.documentAnchor.initApiDocSimpleList();
    }
  },
};
</script>

<style scoped>

</style>
