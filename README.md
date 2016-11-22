```
//进度条（定时增加）

import Function

progress1.progress = 0

NSTimer.scheduledTimerWithTimeUnterval(1,target:self,selector:"changeProgress;",userInfo:nil,repeats:true)

func changeProgress(sender:NSTimer){

 progress1.progress += 0.1

 if(progress1.progress>=1){

 sender.invalidate()

 }

}

//字符串转换

NSString(format:"%g",sender.value)

//警告弹框

UIAlertView(title:"确定关闭",message:"是否关闭当前窗体",delegate:self,cancekButtonTite:"确认").show()

var alertView = UIAlertView(title:"hello",message:"Helloeveryone",delegate:self,cancekButtonTitle:"OK",otherButtonTitles:"Cancel","dfd","dfd")

//警告框样式＋文本框

alerView.alertViewStyle = UIAlertViewStyle.LoginAndPasswordInput

alertView.show()

func alerView(alerView:UIAlertView,clickedButtonAtIndex buttonIndex:int){

 UIAlertView(title:"cliced",message:"Button \(buttonIndex) clicked",delegate:nil,cancekButtonTitle:"OK").show()

 var inputValue = alerView.textFieldAtIndex(0)?.text

 //UIAlertView(title:"Value",message:"Value \(inputValue) clicked",delegate:nil,cancekButtonTite:"OK").show()

}

//UIActionSheet

class ViewController:UIViewController,UIActionSheetDelegate{

 @IBAction func actionButtonClick(sender:UIButton){

 var actionSheet = UIActionSheet(title:"ActionSheet",delegate:self,cancekButtonTitle:"Cancel",destructiveButtonTitle:"OK")

 actionSheet.actionSheetStyle = UIActionSheetStyle.Default

 actionSheet.showInView(self.view)

 }

 func actionSheet(actionSheet:UIActionSheet,clickedButtonAtIndex buttonIndex:Int){

 UIAlertView(title:"你点击了",message:"你点击了Button:\(buttonIndex)",delegate:nil,cancekButtonTitle:"Cancel").show()

 }



}

//UIDatePicker时间列表

@IBAction func valueChanged(sender:UIDatePicker){

 //格式化时间成字符串

 var format = NSDateFormatter()

 //设置日期格式

 //format = NSDateFormatterStyle.shortStyle

 form.dateStyle = "yyy年MM月dd日，HH小时mm分ss秒"

 //把datepicker的date日期转为String

 var dateStr = format.stringFromDate(sender.date)

 NSLog(dateStr)

}

 //倒计UIDatePicker

@IBOutlet var datepicker1:UIDatePicker!

@IBAction func buttoon1Click(sender:UIButton){

 //每一次点击按钮，分钟减少为1分钟

 datepicker1.countDownDuration -= 60

}

//UIPickerView 实现UIPickerViewDataSource,UIPickerViewDelegate方法

import UIKit

class ViewController: UIViewController,UIPickerViewDataSource,UIPickerViewDelegate{

 //定义数据源

 var province = ["四川","云南","广东","广西"]

 var city = ["四川":["成都","绵阳","广元","宜宾"],"云南":["昆明","大理","丽江"],"广东":["广州","佛山","东莞"],"广西":["南宁","桂林"]]

 var selectValue = ""

 @IBOutlet var pickerView1: UIPickerView!

 override func viewDidLoad() {

 super.viewDidLoad()

 // Do any additional setup after loading the view, typically from a nib.

 pickerView1.dataSource = self

 pickerView1.delegate = self

 }

 //设定列数

 func numberOfComponentsInPickerView(pickerView: UIPickerView) -> Int {

 return 2

 }

 //设定每列行数

 func pickerView(pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {

 if(component == 0){//第一列

 return province.count

 }else{//第二列

 if(city[selectValue] != nil){

 return city[selectValue]!.count

 }else{

 return 0

 }

 }

 }

 //显示值

 func pickerView(pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String! {

 if(component == 0){

 return province[row]

 }else{

 if(city[selectValue] != nil){

 return city[selectValue]![row]

 }else{

 return "?"

 }

 }

 }

 //选择事件

 func pickerView(pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {

 if(component == 0){

 selectValue = province[row]

 pickerView1.reloadComponent(1)//重新加载第2列

 pickerView1.selectRow(0, inComponent: 1, animated: true)//选择第二列的第一行

 }

 }

}

//UIWebView浏览器

/*

 1.加载网页方法、停止，上一步，下一步，goBack,goFarword

 2.事件能坚挺浏览器状态

 */

import UIKit

class ViewController: UIViewController,UIWebViewDelegate {



 @IBOutlet var textFiled1: UITextField!

 @IBAction func reloadButtonClick(sender: AnyObject) {

 webView1.reload()

 }

 @IBAction func goButtonClick(sender: AnyObject) {

 webView1.loadRequest(NSURLRequest(URL: NSURL(string: textFiled1.text)!))

 }

 @IBAction func forwardButtonClick(sender: AnyObject) {

 webView1.goForward()

 }

 @IBAction func backButtonClick(sender: AnyObject) {

 webView1.goBack()

 }

 @IBOutlet var webView1: UIWebView!

 override func viewDidLoad() {

 super.viewDidLoad()

 // Do any additional setup after loading the view, typically from a nib.

 webView1.delegate = self



 //webView1.loadHTMLString("<html><h1>hello</h1></html>", baseURL: NSURL(string: "http://www.baidu.com"))



 }



 func webViewDidStartLoad(webView: UIWebView) {

 NSLog("did start load")

 }



 func webViewDidFinishLoad(webView: UIWebView) {

 NSLog("did finish load")

 }

 override func didReceiveMemoryWarning() {

 super.didReceiveMemoryWarning()

 // Dispose of any resources that can be recreated.

 }

}

//工具栏UIToolbar

/*

 Item－－Bar Button Item

 间隔－－Flexible Space Bar Button Item

 固定间隔--fixed Space Bar Button Item

 */



```
