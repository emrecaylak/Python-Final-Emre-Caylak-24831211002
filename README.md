# Python-Final-Emre-Caylak-24831211002

06.01.2025

GAZİ ÜNİVERSİTESİ 
MİMARLIK FAKÜLTESİ
ŞEHİR VE BÖLGE PLANLAMA ANABİLİM DALI
PLANLAMADA COĞRAFİ BİLGİ SİSTEMLERİ
2024-2025 EĞİTİM ÖĞRETİM YILI – GÜZ YARIYILI
CBS 5061 PYTHON İLE COĞRAFİ BİLGİ SİSTEMLERİ PROGRAMLAMA VE YAZILIM GELİŞTİRME DERSİ
FİNAL TESLİMİ

DERS SORUMLUSU: Dr. Öğr. Üyesi Kadriye Burcu YAVUZ
HAZIRLAYAN: Emre ÇAYLAK (24831211002)

GİRİŞ
Bu çalışma kapsamında “Geospatial School” adlı YouTube kanalının “QGIS Python (PyQGIS) - Loading and symbolizing raster layers” adlı videosunda anlatılanlar; Aydın İli, Bozdoğan İlçesi, Kara Ahmetler Mahallesinde bulunan bir alanın dem verisi QGIS yazılımı kullanılarak Python kodu ile oluşturulmuş, renklendirilmiş ve görselleştirilmiştir (URL-1).

YÖNTEM
1) QGIS yazılımında mekansal analiz yapılması ve hazırlanan kodun Python eklentisine tanıtarak görselleştirilmesi.
•	Öncelikle QGIS üzerinden raster dosyası .tif uzantısıyla aktarılmıştır. 
•	Ardından semboloji, renk rampası ve raster shader’ları python koduyla tanıtılarak çalıştırıldığında karşılaşılan görüntü “1.jpg” ve “2.jpg” dosyalarındaki ekran görüntülerinde gösterilmiştir.
•	Bu ekran görüntülerinde belirtilen çıktılar “dem.tif” ve “dem_result.tif” olmak üzere kaydedilmiştir.

2) İlgili görselin ve izlenen adımların GitHub hesabında oluşturulan “Python - Final - Emre Çaylak (24831211002)“adlı repository’de hazırlanan Python koduyla birlikte “Readme.md” dosyası içerisinde açıklanması.
•	Ödev kapsamında hazırlanan belgeler GitHub hesabı üzerinden bir repository oluşturularak içerisine aktarılmıştır (URL-2).
•	Hazırlanan repository’nin içerisine uygulama aşamasında oluşturulan ekran görüntüleri ve çıktılar aktarılmıştır.
•	“Readme.md” dosyası içerisinde uygulamanın açıklaması ve kullanılan Python kodu belirtilmiştir:

PYTHON KODU

import sys
sys.version

#Loading the raster document
fn = 'C:/Users/HP/Desktop/dem.tif'
fi = QFileInfo(fn)
fname = fi.baseName()
rlayer = iface.addRasterLayer(fn, fname)
stats = rlayer.dataProvider() bandStatistics(1, QgsRasterBandStats.All)
min = stats.minimumValue
max = stats.maximumValue

#Symbolizing the raster document
fnc = QgsColorRampShader()
fnc.setColorRampType(QgsColorRampShader.Interpolated)

#Creating color ramp items
lst[QgsColorRampShader.ColorRampItem(min, QColor(0, 255, 0)), \
QgsColorRampShader.ColorRampItem(max, QColor(255, 255, 0))]

#Creating the raster shader
fnc.setColorRampItemList(lst)
shader = QgsRasterShader
shader.setRasterShaderFunction(fnc)
renderer = QfsSingleBandPseudoColorRenderer(rplayer.dataProvider(), 1, shader)
rlayer.setRenderer(renderer)

