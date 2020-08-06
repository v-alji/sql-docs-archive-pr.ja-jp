---
title: 画像デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a177b114e331a817427fbd2ce703afa21390a9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742997"
---
# <a name="image-device-information-settings"></a>画像デバイス情報設定
  次の表は、IMAGE 形式で表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**[列]**|レポートに設定する列の数。 この値により、レポートの元の設定はオーバーライドされます。|  
|**ColumnSpacing**|レポートに設定する列の間隔。 この値により、レポートの元の設定はオーバーライドされます。|  
|`DpiX`|出力画像の水平方向の解像度。 既定値は **96**です。 、、 `BMP` 、およびの各出力形式に適用さ `GIF` `PNG` `TIFF` れます。|  
|`DpiY`|出力画像の垂直方向の解像度。 既定値は **96**です。 、、 `BMP` 、およびの各出力形式に適用さ `GIF` `PNG` `TIFF` れます。|  
|**EndPage**|表示するレポートの最後のページ。 既定値は `StartPage` の値です。|  
|**MarginBottom**|レポートに設定する下余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**MarginLeft**|レポートに設定する左余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**MarginRight**|レポートに設定する右余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**MarginTop**|レポートに設定する上余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**OutputFormat**|[!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) でサポートされるいずれかの出力形式。`BMP`、`EMF`、`GIF`、`JPEG`、`PNG`、または `TIFF` です。|  
|**PageHeight**|レポートに設定するページの高さ (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`11in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**PageWidth**|レポートに設定するページの幅 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`8.5in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**PrintDpiX**|出力画像の水平方向の解像度。 既定値は `300` です。 拡張メタファイル () の `EMF` 出力形式に適用されます。|  
|**PrintDpiY**|出力画像の垂直方向の解像度。 既定値は `300` です。 拡張メタファイル () の `EMF` 出力形式に適用されます。|  
|`StartPage`|表示するレポートの最初のページ。 値 `0` はすべてのページを表示することを示します。 既定値は `1` です。|  
  
## <a name="see-also"></a>参照  
 [表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Configで表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
