---
title: DatabaseQueryTimeout プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e92e3e0f6752ea99fe89c962ebe96e343c0195b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737657"
---
# <a name="databasequerytimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d441e-102">DatabaseQueryTimeout プロパティ (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d441e-102">DatabaseQueryTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d441e-103">レポート サーバーで、コマンドが失敗した、または処理時間が長すぎると見なされるまでの、経過秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d441e-103">Specifies the number of seconds that must elapse before the report server assumes the command failed or took too much time to perform.</span></span> <span data-ttu-id="d441e-104">レポート サーバーは、レポートのデータ ソースではなく、SQL カタログに対するクエリの時間を計測しています。</span><span class="sxs-lookup"><span data-stu-id="d441e-104">The report server is timing the querying against the SQL catalog, not a data source for the report.</span></span> <span data-ttu-id="d441e-105">読み取りと書き込みが可能です。</span><span class="sxs-lookup"><span data-stu-id="d441e-105">Read/write.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d441e-106">構文</span><span class="sxs-lookup"><span data-stu-id="d441e-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="d441e-107">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="d441e-107">Property Values</span></span>  
 <span data-ttu-id="d441e-108">クエリを実行することが許されている秒数を表す 32 ビットの符号なし `integer` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d441e-108">A 32-bit unsigned `integer` object that represents the number of seconds that the query is allowed to run.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="d441e-109">コード例</span><span class="sxs-lookup"><span data-stu-id="d441e-109">Example Code</span></span>  
 [<span data-ttu-id="d441e-110">MSReportServer_ConfigurationSetting クラス</span><span class="sxs-lookup"><span data-stu-id="d441e-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="d441e-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="d441e-111">Requirements</span></span>  
 <span data-ttu-id="d441e-112">**名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d441e-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d441e-113">参照</span><span class="sxs-lookup"><span data-stu-id="d441e-113">See Also</span></span>  
 [<span data-ttu-id="d441e-114">MSReportServer_ConfigurationSetting メンバー</span><span class="sxs-lookup"><span data-stu-id="d441e-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
