---
title: Version プロパティ (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Version property
ms.assetid: eea6bfe9-3130-4272-b3c2-c334349a7afd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4db0b3d01114329cb43bc25e448755806668e779
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639855"
---
# <a name="version-property-wmi-msreportserver_instance"></a><span data-ttu-id="ece65-102">Version プロパティ (WMI MSReportServer_Instance)</span><span class="sxs-lookup"><span data-stu-id="ece65-102">Version Property (WMI MSReportServer_Instance)</span></span>
  <span data-ttu-id="ece65-103">Major.Minor.Build.Revision 形式でレポート サーバーのバージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="ece65-103">Returns the version of the report server in the format Major.Minor.Build.Revision.</span></span> <span data-ttu-id="ece65-104">読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="ece65-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece65-105">構文</span><span class="sxs-lookup"><span data-stu-id="ece65-105">Syntax</span></span>  
  
```vb  
Public Dim Version As String  
```  
  
```csharp  
public string Version;  
```  
  
## <a name="property-value"></a><span data-ttu-id="ece65-106">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="ece65-106">Property Value</span></span>  
 <span data-ttu-id="ece65-107">レポート サーバーのバージョンを表す `string`。</span><span class="sxs-lookup"><span data-stu-id="ece65-107">A `string` that contains the version of the report server.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="ece65-108">コード例</span><span class="sxs-lookup"><span data-stu-id="ece65-108">Example Code</span></span>  
 [<span data-ttu-id="ece65-109">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="ece65-109">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="ece65-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="ece65-110">Requirements</span></span>  
 <span data-ttu-id="ece65-111">**名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ece65-111">**Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece65-112">参照</span><span class="sxs-lookup"><span data-stu-id="ece65-112">See Also</span></span>  
 [<span data-ttu-id="ece65-113">MSReportServer_Instance メンバー</span><span class="sxs-lookup"><span data-stu-id="ece65-113">MSReportServer_Instance Members</span></span>](msreportserver-instance-members.md)  
  
  
