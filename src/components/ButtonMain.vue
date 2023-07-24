<script>
    export default {
        name: 'ButtonMain',
        methods: {
            onClick() {
                this.$emit('button-click')
            }
        },
        props: {
                text: {
                type: String,
                required: true
              },
                color: {
                type: String,
              },
              type: {
                  type: String,
              },
        }
    }
</script>

<template>
    <button type="type" class="btn" :style="{background: color}" @click="onClick()">{{ text }}</button>
</template>
    
<style scoped>
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>