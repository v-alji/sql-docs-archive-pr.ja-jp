---
title: 結論 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1e6fde6-c3a7-4b91-b176-fa465325dd21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 906f9f10c541e7662d5573fd242a84f37483166e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720511"
---
# <a name="conclusion"></a><span data-ttu-id="e8a7a-102">まとめ</span><span class="sxs-lookup"><span data-stu-id="e8a7a-102">Conclusion</span></span>
  <span data-ttu-id="e8a7a-103">このチュートリアルでは、SQL Server Integration Services (SSIS)、マスター データ サービス (MDS)、および Data Quality Services (DQS) を組み合わせて、Enterprise Information Management (EIM) ソリューションのサンプルを実装する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="e8a7a-103">In this tutorial, you have learned how to use SQL Server Integration Services (SSIS), Master Data Services (MDS), and Data Quality Services (DQS) together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="e8a7a-104">まず、Data Quality Client ツールを使用して仕入先についてのナレッジを含む DQS ナレッジ ベースを作成し、ナレッジ ベースに対して Excel ファイル内の入力済みの仕入先データをクレンジングして、ナレッジ ベースの照合ポリシーを使用して仕入先データを一致させてデータ内の重複項目を特定および削除しました。</span><span class="sxs-lookup"><span data-stu-id="e8a7a-104">First, you used the Data Quality Client tool to create a DQS knowledge base with the knowledge about suppliers, cleansed the input supplier data in an excel file against the knowledge base, and then matched the supplier data by using a matching policy in the knowledge base to identify and remove duplicates in the data.</span></span> <span data-ttu-id="e8a7a-105">次に、Excel 用の MDS アドインを使用して、クレンジングおよび一致済みの仕入先リストを MDS に保存しました。</span><span class="sxs-lookup"><span data-stu-id="e8a7a-105">Next, by using the MDS Add-in for Excel, you stored the cleansed and matched supplier list in MDS.</span></span> <span data-ttu-id="e8a7a-106">最後に、SSIS ソリューションを作成することで、入力データの受信、データのクレンジングと照合、およびマスター データの MDS への保存というプロセス全体を自動化しました。</span><span class="sxs-lookup"><span data-stu-id="e8a7a-106">Finally, you automated the whole process of receiving input data, cleansing and matching the data, and storing the master data in MDS by creating an SSIS solution.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="e8a7a-107">詳細情報:</span><span class="sxs-lookup"><span data-stu-id="e8a7a-107">For more information:</span></span>  
  
 [<span data-ttu-id="e8a7a-108">Enterprise Information Management (EIM): SSIS、DQS、および MDS の統合 (ビデオ)</span><span class="sxs-lookup"><span data-stu-id="e8a7a-108">Enterprise Information Management (EIM): Bringing together SSIS, DQS, and MDS (Video)</span></span>](https://go.microsoft.com/fwlink/?LinkId=258672)  
  
  
