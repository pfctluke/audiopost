# 测试

this.$http.post(`[URL]`, JSON.stringify({
  [PARAMNAME]: [PARAM]
}), {headers: {'Content-Type': 'application/json'}}).then((response) => {
  _self.readBlobAsDataURL(response.body, function(d){
    audio.src = d

    function setEndedPlay () {
      if (audio.ended) {
        _self.audioStatus = '播放'
        clearInterval(timer)
      }
    }
    let timer = setInterval(setEndedPlay,1000)
    if (_self.audioStatus === '暂停') {
      audio.pause()
      _self.audioStatus = '播放'
    } else {
      audio.play()
      _self.audioStatus = '暂停'
    }
  })
})
