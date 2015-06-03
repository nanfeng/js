//引入phpqrcode库文件

include('phpqrcode.php'); 

// 二维码数据 

$data = 'http://www.baidu.com'; 

// 生成的文件名 

$filename = 'baidu.png'; 

// 纠错级别：L、M、Q、H 

$errorCorrectionLevel = 'L';  

// 点的大小：1到10 

$matrixPointSize = 4;  

//创建一个二维码文件 

QRcode::png($data, $filename, $errorCorrectionLevel, $matrixPointSize, 2);

//输入二维码到浏览器

QRcode::png($data); 


phpqrcode.php提供了一个关键的png()方法，其中
参数$text表示生成二位的的信息文本；
参数$outfile表示是否输出二维码图片 文件，默认否；
参数$level表示容错率，也就是有被覆盖的区域还能识别，分别是 L（QR_ECLEVEL_L，7%），M（QR_ECLEVEL_M，15%），Q（QR_ECLEVEL_Q，25%），H（QR_ECLEVEL_H，30%）； 
参数$size表示生成图片大小，默认是3；参数$margin表示二维码周围边框空白区域间距值；
参数$saveandprint表示是否保存二维码并显示
public static function png($text, $outfile=false, $level=QR_ECLEVEL_L, $size=3, $margin=4, $saveandprint=false)    
{   
    $enc = QRencode::factory($level, $size, $margin);   
    return $enc->encodePNG($text, $outfile, $saveandprint=false);   
}
