<template>
  <div id="qrcode">
    <div>
      <p>二维码大小</p>
      <Input v-model="qrSize" type="textarea" :rows="1" placeholder="二维码大小,默认200" />
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
      :logoScale="0.2"
      :text="content"
      colorDark="#000"
      colorLight="#fff"
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
      imgName: '',
      visible: false,
      logoFile: '',
      value: 'www.baidu.com',
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
