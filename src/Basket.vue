<script>
import { h } from "vue";

export default {
  props: ["width", "height", "rows", "columns", "gap"],
  render() {
    let rects = [];

    let padding = 20;

    let offset = 0;

    for (let row = 0; row < this.rows; row++) {
      let left = padding;

      if (row > 0) {
        if (row % 2 === 0) {
          offset += this.width / 2 - this.height / 2 + this.height + this.gap;
        } else {
          offset += this.height / 2 - this.width / 2 + this.width + this.gap;
        }
      }

      for (let col = 0; col < this.columns; col++) {
        let top = padding + offset;
        let width = this.width;
        let height = this.height;

        if (row % 2 === 0) {
          if (col % 2 === 0) {
            width = this.height;
            height = this.width;

            top += width / 2 - height / 2;
          }

          if (col > 0) {
            left += height + this.gap;
          }
        } else {
          if (col % 2 === 0) {
            left += height / 2 - width / 2;
          } else {
            width = this.height;
            height = this.width;

            top += width / 2 - height / 2;
          }

          if (col > 0) {
            if (col % 2 === 0) {
              left += width + this.gap;
              left += height / 2 - width / 2;
            } else {
              left += height + this.gap;
            }
          }
        }

        rects.push(
          h("div", {
            class: "rect",
            style: {
              width: `${width}px`,
              height: `${height}px`,
              top: `${top}px`,
              left: `${left}px`,
            },
          })
        );
      }
    }

    return rects;
  },
};
</script>

<style scoped>
.rect {
  background-color: #88ffef;
  width: 50px;
  height: 50px;
  position: fixed;
}
</style>
