---
title: URL アクセスを使用してレポート履歴スナップショットを表示する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 67854a39ab7e38289627d03ac00cc4b2a6dca6f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640752"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a><span data-ttu-id="a8438-102">URL アクセスを使用してレポート履歴スナップショットを表示する</span><span class="sxs-lookup"><span data-stu-id="a8438-102">Render a Report History Snapshot Using URL Access</span></span>
  <span data-ttu-id="a8438-103">*rs:Snapshot* パラメーターを指定し、その値を有効なスナップショット ID に設定することによって、レポート履歴スナップショットに基づくレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a8438-103">You can render a report based on a report history snapshot by supplying the *rs:Snapshot* parameter and setting its value to a valid snapshot ID.</span></span> <span data-ttu-id="a8438-104">パラメーターの値は、国際標準化機構 (ISO) 8601 の標準に基づく、YYYY-MM-DDTHH:MM:SS の形式です。</span><span class="sxs-lookup"><span data-stu-id="a8438-104">The parameter value is in the format YYYY-MM-DDTHH:MM:SS, based on the International Organization for Standardization (ISO) 8601 standard.</span></span>  
  
 <span data-ttu-id="a8438-105">このパラメーターを省略した場合、レポートは、レポート サーバーのレポート実行およびキャッシュ管理オプションの設定に基づいて表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8438-105">If you omit this parameter, the report is rendered according to the report execution and cache management option settings of the report server.</span></span> <span data-ttu-id="a8438-106">レポートの実行方法については、「 [レポート処理プロパティの設定](report-server/set-report-processing-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8438-106">For more information about report execution, see [Set Report Processing Properties](report-server/set-report-processing-properties.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8438-107">例</span><span class="sxs-lookup"><span data-stu-id="a8438-107">Example</span></span>  
 <span data-ttu-id="a8438-108">次の例は、レポート履歴スナップショットを取得する URL を示します。</span><span class="sxs-lookup"><span data-stu-id="a8438-108">The following example shows a URL that retrieves a report history snapshot:</span></span>  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8438-109">参照</span><span class="sxs-lookup"><span data-stu-id="a8438-109">See Also</span></span>  
 <span data-ttu-id="a8438-110">[URL アクセス (SSRS)](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a8438-110">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="a8438-111">URL アクセス パラメーター リファレンス</span><span class="sxs-lookup"><span data-stu-id="a8438-111">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
