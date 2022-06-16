# 비디오 재생 앱/AVPlayerViewController

**이 앱은 AVPlayerViewController를 사용하여 앱 내부에 저장되어 있는 비디오 파일뿐만 아니라 외부에 링크된 비디오 파일도 간단하게 재생할 수 있습니다.**

***
```
    @IBAction func btnPlayInternalMovie(_ sender: UIButton) {
        let filePath: String? = Bundle.main.path(forResource: "FastTyping", ofType: "mp4")
        let url = NSURL(fileURLWithPath: filePath!)
        let playerController = AVPlayerViewController() 
        let player = AVPlayer(url: url as URL)
        playerController.player = player
        self.present(playerController, animated: true){
            player.play()
            }
     }
```
우선 비디오 파일명을 사용하여 비디오가 저장된 앱 내부의 파일 경로를 받아옵니다.
앱 내부의 파일명을 NSURL 형식으로 변경합니다.
AVPlayerViewController의 인스턴스를 생성합니다.
앞에서 얻은 비디오 URL로 초기화된 AVPlayer의 인스턴스를 생성합니다.
AVPlayerViewController의 player 속성에 앞 문단에서 생성한 AVPlayer 인스턴스를 할당합니다.
비디오를 재생합니다.
