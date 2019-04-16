<template>
  <div id="qrcode">
    <div>
      <p>空白区的颜色, 默认白色#000</p>
      <Input v-model="colorLight" type="textarea" :rows="1" placeholder="#000" />
    </div>
    <div>
      <p>实点的颜色, 默认黑色#fff</p>
      <Input v-model="colorDark" type="textarea" :rows="1" placeholder="#fff" />
    </div>
    <div>
      <p>logo大小,默认0.2</p>
      <Input v-model="logoSize" type="textarea" :rows="1" placeholder="0.2" />
    </div>
    <div>
      <p>二维码大小,默认200</p>
      <Input v-model="qrSize" type="textarea" :rows="1" placeholder="200" />
    </div>
    <div>
      <p>二维码内容</p>
      <Input v-model="content" type="textarea" :rows="5" placeholder="二维码内容" />
    </div>
    <div>
      <!--colorDark="#f67b29"-->
      <!--保存图片按钮-->
      <vue-qr
      :logoCornerRadius="0.1"
      :logoSrc="imagePath"
      :logoScale="logoSize"
      :text="content"
      :colorDark="colorDark"
      :colorLight="colorLight"
      :size="qrSize"
      :margin="0"
      :whiteMargin="true"
      :dotScale="1"></vue-qr>
      <p class="">二维码</p>
      <!--保存图片按钮-->
    </div>
    <div>
      <Button type="success" @click="downloadImg">保存图片</Button>
    </div>
  </div>
</template>

<script>
import VueQr from 'vue-qr'
export default {
  data () {
    return {
      content: '请输入二维码内容',
      qrSize: '200',
      logoSize: '0.2',
      imgName: '',
      visible: false,
      logoFile: '',
      colorLight: '#000',
      colorDark: '#fff',
      imagePath: require('../assets/logo.png')
    }
  },

  created () {},
  components: {
    VueQr
  },

  methods: {
    downloadImg () {
      var oQrcode = document.querySelector('#qrcode img')
      var url = oQrcode.src
      var a = document.createElement('a')
      var event = new MouseEvent('click')
      a.download = '二维码'
      a.href = url
      a.dispatchEvent(event)
    }
  }

}
</script>
