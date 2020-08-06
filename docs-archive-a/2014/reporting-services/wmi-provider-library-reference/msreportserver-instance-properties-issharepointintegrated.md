---
title: IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0c92ebe586d37053b47f90ca98c31b3068a7b91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639857"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a><span data-ttu-id="9cafb-102">IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="9cafb-102">IsSharePointIntegrated Property (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="9cafb-103">レポート サーバーが SharePoint 統合モードであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9cafb-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="9cafb-104">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降、このプロパティは常に `False` を返します。これは、SharePoint モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスは SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。</span><span class="sxs-lookup"><span data-stu-id="9cafb-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cafb-105">構文</span><span class="sxs-lookup"><span data-stu-id="9cafb-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="9cafb-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="9cafb-106">Property Values</span></span>  
 <span data-ttu-id="9cafb-107">レポート サーバーが SharePoint 統合モードであるかどうかを示す `Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="9cafb-107">A `Boolean` value that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cafb-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="9cafb-108">Requirements</span></span>  
 <span data-ttu-id="9cafb-109">**名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cafb-109">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cafb-110">参照</span><span class="sxs-lookup"><span data-stu-id="9cafb-110">See Also</span></span>  
 <span data-ttu-id="9cafb-111">[MSReportServer_Instance メンバー](msreportserver-instance-members.md) </span><span class="sxs-lookup"><span data-stu-id="9cafb-111">[MSReportServer_Instance Members](msreportserver-instance-members.md) </span></span>  
 [<span data-ttu-id="9cafb-112">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="9cafb-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
  
