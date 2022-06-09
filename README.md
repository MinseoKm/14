# 14
14
import UIKit
import AVKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }
    
    @IBAction func btnPlayInternalMovie(_ sender: UIButton) {
        // 내부파일 mp4
        let filePath: String? = Bundle.main.path(forResource: "FastTyping", ofType: "mp4") // 비디오 파일명을 이용하여 저장된 앱 내부 파일 경로 받는다.
        
        let url = NSURL(fileURLWithPath: filePath!) // 앱 내부의 파일명을 NSURL 형식으로 변경
        
        playVideo(url: url) // 앞에서 얻은 url
    }
    @IBAction func btnPlayExternalMovie(_ sender: UIButton) {
        // 외부 파일 mp4
        // 내부 파일 실행과 실행 url만 다를뿐, 나머지는 동일
        
        let url = NSURL(string: "https://dl.dropboxusercontent.com/s/e38auz050w2mvud/Fireworks.mp4")!
        
        playVideo(url: url)
    }
    
    private func playVideo(url: NSURL) {
    // 공통된 부분 비디오 재생 함수로 코드 재사용
        let playerController = AVPlayerViewController() // AVPlayerViewController 인스턴스 생성
        
        let player = AVPlayer(url: url as URL) // 앞에서 얻은 비디오 URL로 초기화된 AVPlayer의 인스턴스 생성
        playerController.player = player // AVPlayerViewController 속성에 위 코드에서 생성한 AVPlayer 인스턴스 할당
        
        self.present(playerController, animated: true) {
            player.play() // 비디오 재생
        }
    }
}
