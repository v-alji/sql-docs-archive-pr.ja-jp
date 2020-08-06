---
title: IntelliSense
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7d6b0f60-c6ac-4f71-a9d0-fc3c2ffa7e91
author: rothja
ms.author: jroth
ms.openlocfilehash: 6be9f1311937affbb7358dd0e7ca96af5f7bffdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644978"
---
# <a name="intellisense-sql-server-management-studio"></a><span data-ttu-id="99843-102">IntelliSense (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="99843-102">IntelliSense (SQL Server Management Studio)</span></span>
  <span data-ttu-id="99843-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のエディターは [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense オプションをサポートしているので、入力操作を減らし、構文情報をすばやく提示し、複合式の区切りをわかりやすく表示できます。</span><span class="sxs-lookup"><span data-stu-id="99843-103">The editors in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] support [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense options that reduce typing, provide quick access to syntax information, or make it easier to view the delimiters of complex expressions.</span></span>  
  
## <a name="benefits-of-intellisense"></a><span data-ttu-id="99843-104">IntelliSense の利点</span><span class="sxs-lookup"><span data-stu-id="99843-104">Benefits of IntelliSense</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="99843-105">IntelliSense には、言語リファレンスに簡単にアクセスするためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="99843-105">IntelliSense provides an array of options that make language references easily accessible.</span></span> <span data-ttu-id="99843-106">コーディング時に言語要素を検索する場合でも、エディターでの作業を中断する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="99843-106">When coding, you do not need to leave the editor to perform searches on language elements.</span></span> <span data-ttu-id="99843-107">コンテキストを保持したまま、必要な情報を探し、言語要素を直接コードに挿入できます。IntelliSense で入力を補完することもできます。</span><span class="sxs-lookup"><span data-stu-id="99843-107">You can keep your context, find the information you need, insert language elements directly into your code, and even have IntelliSense complete your typing for you.</span></span>  
  
## <a name="intellisense-tasks"></a><span data-ttu-id="99843-108">IntelliSense のタスク</span><span class="sxs-lookup"><span data-stu-id="99843-108">IntelliSense Tasks</span></span>  
  
|<span data-ttu-id="99843-109">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="99843-109">Task Description</span></span>|<span data-ttu-id="99843-110">トピック</span><span class="sxs-lookup"><span data-stu-id="99843-110">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="99843-111">入力候補オプション、IntelliSense をオフにする Transact-SQL スクリプトのサイズなどの、IntelliSense オプションの構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99843-111">Describes how to configure IntelliSense options such as statement completion options or the size of Transact-SQL scripts for which you want IntelliSense turned off.</span></span>|[<span data-ttu-id="99843-112">IntelliSense の構成 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="99843-112">Configure IntelliSense &#40;SQL Server Management Studio&#41;</span></span>](configure-intellisense-sql-server-management-studio.md)|  
|<span data-ttu-id="99843-113">パラメーター ヒントを使用して、関数またはストアド プロシージャのパラメーターの数、名前、およびサイズに関する情報を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99843-113">Describes how to use Parameter Info to get information about the number, names, and sizes of parameters for a function or stored procedure.</span></span>|[<span data-ttu-id="99843-114">パラメーター ヒント &#40;IntelliSense&#41;</span><span class="sxs-lookup"><span data-stu-id="99843-114">Parameter Info &#40;IntelliSense&#41;</span></span>](parameter-info-intellisense.md)|  
|<span data-ttu-id="99843-115">クイック ヒントを使用して、識別子 (テーブルやビューの名前など) を説明するツールヒントを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99843-115">Describes how to use Quick Info to get tooltips that describe an identifier (such as a table or view name).</span></span>|[<span data-ttu-id="99843-116">クイック ヒント &#40;IntelliSense&#41;</span><span class="sxs-lookup"><span data-stu-id="99843-116">Quick Info &#40;IntelliSense&#41;</span></span>](quick-info-intellisense.md)|  
|<span data-ttu-id="99843-117">名前の一部を入力し、それと同じ文字列で始まる名前のオブジェクトの短い一覧を取得した後で、識別子の残り部分を IntelliSense に補完させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99843-117">Describes how to have IntelliSense complete the rest of an identifier after you have typed in enough of the name to get a short list of objects whose names start with the same string.</span></span>|[<span data-ttu-id="99843-118">入力候補 &#40;IntelliSense&#41;</span><span class="sxs-lookup"><span data-stu-id="99843-118">Complete Word &#40;IntelliSense&#41;</span></span>](complete-word-intellisense.md)|  
|<span data-ttu-id="99843-119">IntelliSense が区切り記号のペアの両端を識別する方法と、ペアの片方の端からもう一方の端へ移動する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="99843-119">Describes how IntelliSense can identify both ends of a pair of delimiters, and how you can jump between the two ends of the pair.</span></span>|[<span data-ttu-id="99843-120">構文ペアの自動照合</span><span class="sxs-lookup"><span data-stu-id="99843-120">Automatic Matching of Syntax Pairs</span></span>](automatic-matching-of-syntax-pairs.md)|  
|<span data-ttu-id="99843-121">IntelliSense が動作しない状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="99843-121">Describes the conditions under which IntelliSense may not work.</span></span>|[<span data-ttu-id="99843-122">IntelliSense のトラブルシューティング (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="99843-122">Troubleshooting IntelliSense (SQL Server Management Studio)</span></span>](troubleshooting-intellisense.md)|  
  
## <a name="see-also"></a><span data-ttu-id="99843-123">参照</span><span class="sxs-lookup"><span data-stu-id="99843-123">See Also</span></span>  
 [<span data-ttu-id="99843-124">クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="99843-124">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
