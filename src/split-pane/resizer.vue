<template>
	<div :class="classes"></div>
</template>

<script>
  export default {
    props: {
      split: {
        validator(value) {
          return ['vertical', 'horizontal'].indexOf(value) >= 0
        },
        required: true
      },
      className: String
    },
    computed: {
      classes() {
        const classes = ['splitter-pane-resizer', this.split, this.className]
        return classes.join(' ')
      }
    }
  }
</script>

<style scoped>
	.splitter-pane-resizer {
		-moz-box-sizing: border-box;
		-webkit-box-sizing: border-box;
		box-sizing: border-box;
		background: #000;
		position: absolute;
		z-index: 1;
		-moz-background-clip: padding;
		-webkit-background-clip: padding;
		background-clip: padding-box;
		margin: 0;
		left: 0;
		opacity: 1 !important;
	}

	.splitter-pane-resizer.horizontal {
		margin: -5px 0;
		cursor: row-resize;
		width: 100%;
		height: 6px;
		background: #eee;
		border-top: 1px solid #ddd !important;
		border-bottom: 1px solid #ddd !important;
	}

	.splitter-pane-resizer.vertical {
		height: 100%;
		cursor: col-resize;
		width: 6px;
		background: #eee;
		border-left: 1px solid #ddd !important;
		border-right: 1px solid #ddd !important;
		margin-left: 2px;
	}

	.splitter-pane-resizer.horizontal:before {
		display: block;
		content: "";
		height: 3px;
		width: 40px;
		position: absolute;
		top: 50%;
		left: 50%;
		margin-left: -20px;
		margin-top: -2px;
		border: 1px solid #ccc;
		border-radius: 3px;
		background: #f8f8f8;
	}

	.splitter-pane-resizer.vertical:before {
		display: block;
		content: "";
		height: 40px;
		width: 3px;
		position: absolute;
		top: 50%;
		left: 50%;
		margin-left: -3px;
		margin-top: -2px;
		border: 1px solid #ccc;
		border-radius: 3px;
		background: #f8f8f8;
	}
</style>
