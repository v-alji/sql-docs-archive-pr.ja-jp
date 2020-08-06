---
title: Rswindowsex"Dedprotectionlevel プロパティ (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02ff3bad42ae25adf6cfa563944d89bac2c600e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639856"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="6dc2e-102">RSWindowsExtendedProtectionLevel プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="6dc2e-102">RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="6dc2e-103">レポート サーバーがサポートするように構成されている保護のレベルを示す文字列値を返します。</span><span class="sxs-lookup"><span data-stu-id="6dc2e-103">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="6dc2e-104">このプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="6dc2e-104">This property is read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc2e-105">構文</span><span class="sxs-lookup"><span data-stu-id="6dc2e-105">Syntax</span></span>  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a><span data-ttu-id="6dc2e-106">解説</span><span class="sxs-lookup"><span data-stu-id="6dc2e-106">Remarks</span></span>  
 <span data-ttu-id="6dc2e-107">レポート サーバーがサポートするように構成されている保護のレベルを示す文字列値を返します。</span><span class="sxs-lookup"><span data-stu-id="6dc2e-107">Returns a string value that indicates the level of protection the report server is configured to support.</span></span> <span data-ttu-id="6dc2e-108">WMI プロバイダーの接続先のレポート サーバーが拡張保護をサポートしていない場合は、"" (空の文字列) が返されます。</span><span class="sxs-lookup"><span data-stu-id="6dc2e-108">If the report server that the WMI provider is connected to does not support extended protection, "" (empty string) is returned.</span></span> <span data-ttu-id="6dc2e-109">有効な値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6dc2e-109">The following list shows valid values:</span></span>  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a><span data-ttu-id="6dc2e-110">コード例</span><span class="sxs-lookup"><span data-stu-id="6dc2e-110">Example Code</span></span>  
 [<span data-ttu-id="6dc2e-111">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="6dc2e-111">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a><span data-ttu-id="6dc2e-112">参照</span><span class="sxs-lookup"><span data-stu-id="6dc2e-112">See Also</span></span>  
 <span data-ttu-id="6dc2e-113">[RSWindowsExtendedProtectionScenario プロパティ (WMI MSReportServer_ConfigurationSetting)](rswindowsextendedprotectionscenario-property.md) </span><span class="sxs-lookup"><span data-stu-id="6dc2e-113">[RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md) </span></span>  
 <span data-ttu-id="6dc2e-114">[SetExtendedProtectionSettings メソッド (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md) </span><span class="sxs-lookup"><span data-stu-id="6dc2e-114">[SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md) </span></span>  
 <span data-ttu-id="6dc2e-115">[Reporting Services での認証の拡張保護](../security/extended-protection-for-authentication-with-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="6dc2e-115">[Extended Protection for Authentication with Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md) </span></span>  
 [<span data-ttu-id="6dc2e-116">RSReportServer 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="6dc2e-116">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
