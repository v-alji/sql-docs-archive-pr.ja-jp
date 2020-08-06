---
title: IsSharePointIntegrated プロパティ (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a1f3f38c23546ddf4dfb52c2a3af7c122af10cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643162"
---
# <a name="issharepointintegrated-property-wmi"></a><span data-ttu-id="f7a5b-102">IsSharePointIntegrated プロパティ (WMI)</span><span class="sxs-lookup"><span data-stu-id="f7a5b-102">IsSharePointIntegrated Property (WMI)</span></span>
  <span data-ttu-id="f7a5b-103">レポート サーバーが SharePoint 統合モードであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f7a5b-103">Specifies whether the report server is in SharePoint integrated mode.</span></span> <span data-ttu-id="f7a5b-104">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降、このプロパティは常に `False` を返します。これは、SharePoint モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスは SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。</span><span class="sxs-lookup"><span data-stu-id="f7a5b-104">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], this property always returns `False` because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instances are SharePoint shared services and are not controlled by WMI providers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a5b-105">構文</span><span class="sxs-lookup"><span data-stu-id="f7a5b-105">Syntax</span></span>  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a><span data-ttu-id="f7a5b-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="f7a5b-106">Property Values</span></span>  
 <span data-ttu-id="f7a5b-107">レポート サーバーが SharePoint 統合モードであるかどうかを示す `Boolean` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f7a5b-107">A `Boolean` object that indicates whether the report server is in SharePoint integrated mode.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="f7a5b-108">コード例</span><span class="sxs-lookup"><span data-stu-id="f7a5b-108">Example Code</span></span>  
 [<span data-ttu-id="f7a5b-109">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="f7a5b-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="f7a5b-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f7a5b-110">Requirements</span></span>  
 <span data-ttu-id="f7a5b-111">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7a5b-111">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a5b-112">参照</span><span class="sxs-lookup"><span data-stu-id="f7a5b-112">See Also</span></span>  
 [<span data-ttu-id="f7a5b-113">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="f7a5b-113">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
