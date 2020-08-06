---
title: Rswindowsex"Dedprotectionscenario プロパティ (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84e14d056cc0352b0d1d85bc12c9c873a1b89ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719407"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="2ea61-102">RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="2ea61-102">RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="2ea61-103">レポート サーバーが許可するように構成されている拡張保護のシナリオを示す文字列値を返します。</span><span class="sxs-lookup"><span data-stu-id="2ea61-103">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea61-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ea61-104">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a><span data-ttu-id="2ea61-105">解説</span><span class="sxs-lookup"><span data-stu-id="2ea61-105">Remarks</span></span>  
 <span data-ttu-id="2ea61-106">レポート サーバーが許可するように構成されている拡張保護のシナリオを示す文字列値を返します。</span><span class="sxs-lookup"><span data-stu-id="2ea61-106">Returns a string value that indicates the extended protection scenario the report server is configured to allow.</span></span> <span data-ttu-id="2ea61-107">WMI プロバイダーの接続先のレポート サーバーが拡張保護をサポートしていない場合は、"" (空の文字列) が返されます。</span><span class="sxs-lookup"><span data-stu-id="2ea61-107">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span>  
  
 <span data-ttu-id="2ea61-108">有効な値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2ea61-108">The following list shows valid values:</span></span>  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a><span data-ttu-id="2ea61-109">コード例</span><span class="sxs-lookup"><span data-stu-id="2ea61-109">Example Code</span></span>  
 [<span data-ttu-id="2ea61-110">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="2ea61-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ea61-111">参照</span><span class="sxs-lookup"><span data-stu-id="2ea61-111">See Also</span></span>  
 <span data-ttu-id="2ea61-112">[RSWindowsExtendedProtectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionlevel-property.md) </span><span class="sxs-lookup"><span data-stu-id="2ea61-112">[RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md) </span></span>  
 <span data-ttu-id="2ea61-113">[SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="2ea61-113">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="2ea61-114">[Reporting Services での認証の拡張保護](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="2ea61-114">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="2ea61-115">RSReportServer 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2ea61-115">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
