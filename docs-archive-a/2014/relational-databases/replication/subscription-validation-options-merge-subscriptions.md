---
title: '[サブスクリプションの検証オプション] (マージ サブスクリプション) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 458da0387dbaa1b366348c374748c42946893feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741758"
---
# <a name="subscription-validation-options-merge-subscriptions"></a><span data-ttu-id="0e588-102">[サブスクリプションの検証オプション] (マージ サブスクリプション)</span><span class="sxs-lookup"><span data-stu-id="0e588-102">Subscription Validation Options (Merge Subscriptions)</span></span>
  <span data-ttu-id="0e588-103">**[サブスクリプションの検証オプション]** ダイアログ ボックスを使用すると、検証の際に行数だけを使用するか、行数とバイナリ チェックサムを使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0e588-103">Use the **Subscription Validation Options** dialog box to specify whether validation should use a row count only or a row count and a binary checksum.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0e588-104">Options</span><span class="sxs-lookup"><span data-stu-id="0e588-104">Options</span></span>  
 <span data-ttu-id="0e588-105">**[行数のみを確認する]**</span><span class="sxs-lookup"><span data-stu-id="0e588-105">**Verify the row counts only**</span></span>  
 <span data-ttu-id="0e588-106">選択すると、サブスクライバー側のテーブルとパブリッシャー側のテーブルの行数が同じかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="0e588-106">Select to validate whether the table at the Subscriber has the same number of rows as the table at the Publisher.</span></span> <span data-ttu-id="0e588-107">この方法では、行の内容が一致するかどうかは確認されません。</span><span class="sxs-lookup"><span data-stu-id="0e588-107">This method does not validate that the content of the rows matches.</span></span> <span data-ttu-id="0e588-108">行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。</span><span class="sxs-lookup"><span data-stu-id="0e588-108">Row count validation provides a lightweight approach to validation that can make you aware of issues with your data.</span></span>  
  
 <span data-ttu-id="0e588-109">**[行数を確認し、行データを評価するためにチェックサムを比較する (すべてのサブスクライバーは SQL Server 2000 以降を実行しているサーバー)]**</span><span class="sxs-lookup"><span data-stu-id="0e588-109">**Verify the row counts and compare checksums to verify the row data**</span></span>  
 <span data-ttu-id="0e588-110">パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。</span><span class="sxs-lookup"><span data-stu-id="0e588-110">In addition to taking a count of rows at the Publisher and Subscriber, a checksum of all the data is calculated using the binary checksum algorithm.</span></span> <span data-ttu-id="0e588-111">行数の検証で失敗となった場合、チェックサムは実行されません。</span><span class="sxs-lookup"><span data-stu-id="0e588-111">If the row count fails, the checksum is not performed.</span></span> <span data-ttu-id="0e588-112">このオプションは、では無効です [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0e588-112">This option is not valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e588-113">参照</span><span class="sxs-lookup"><span data-stu-id="0e588-113">See Also</span></span>  
 <span data-ttu-id="0e588-114">[サブスクライバーでデータを検証する](validate-data-at-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="0e588-114">[Validate Data at the Subscriber](validate-data-at-the-subscriber.md) </span></span>  
 [<span data-ttu-id="0e588-115">レプリケートされたデータの検証</span><span class="sxs-lookup"><span data-stu-id="0e588-115">Validate Replicated Data</span></span>](validate-data-at-the-subscriber.md)  
  
  
