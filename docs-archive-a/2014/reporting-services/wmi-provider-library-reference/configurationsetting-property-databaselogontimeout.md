---
title: DatabaseLogonTimeout プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4920f5ef2282478f4d12a19b0806cf6ff9632cac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737668"
---
# <a name="databaselogontimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="7d952-102">DatabaseLogonTimeout プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="7d952-102">DatabaseLogonTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="7d952-103">レポート サーバー データベースへのログインを失敗と判断するまでの待機時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="7d952-103">Specifies the number of seconds to wait before an attempt to log on to the report server database fails.</span></span> <span data-ttu-id="7d952-104">値 **0** は、待ち時間が無限であることを示します。</span><span class="sxs-lookup"><span data-stu-id="7d952-104">A value of **0** indicates an infinite wait time.</span></span> <span data-ttu-id="7d952-105">読み取り専用。</span><span class="sxs-lookup"><span data-stu-id="7d952-105">Read only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d952-106">構文</span><span class="sxs-lookup"><span data-stu-id="7d952-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="7d952-107">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="7d952-107">Property Values</span></span>  
 <span data-ttu-id="7d952-108">秒数を表す 32 ビット符号付き整数オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7d952-108">A 32-bit signed integer object that represents the number of seconds.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="7d952-109">コード例</span><span class="sxs-lookup"><span data-stu-id="7d952-109">Example Code</span></span>  
 [<span data-ttu-id="7d952-110">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="7d952-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="7d952-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="7d952-111">Requirements</span></span>  
 <span data-ttu-id="7d952-112">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d952-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d952-113">参照</span><span class="sxs-lookup"><span data-stu-id="7d952-113">See Also</span></span>  
 [<span data-ttu-id="7d952-114">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="7d952-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
