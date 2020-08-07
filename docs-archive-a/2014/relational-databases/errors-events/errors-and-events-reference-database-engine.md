---
title: エラーおよびイベント リファレンス (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server Database Engine]
- Database Engine [SQL Server], errors
- events [SQL Server Database Engine]
ms.assetid: ea928535-6fd1-4738-a8ed-ffb602f3825e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e991accfd0e6fdd4fa25746499308455eff85ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719976"
---
# <a name="errors-and-events-reference-database-engine"></a><span data-ttu-id="b811e-102">エラーおよびイベント リファレンス (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="b811e-102">Errors and Events Reference (Database Engine)</span></span>

<span data-ttu-id="b811e-103">ここでは、詳細な説明が必要なデータベースエンジンのエラーメッセージについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b811e-103">This section contains selected Database Engine error messages that need further explanation.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="b811e-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b811e-104">In This Section</span></span>  
 <span data-ttu-id="b811e-105">[データベースエンジンイベントとエラー](database-engine-events-and-errors.md)エラーメッセージの形式と、エラーメッセージを表示してアプリケーションにエラーメッセージを返す方法について説明し [!INCLUDE[ssDE](../../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b811e-105">[Database Engine Events and Errors](database-engine-events-and-errors.md) Describes the format of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages and explains how to view error messages and return error messages to applications.</span></span>  
  
 <span data-ttu-id="b811e-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のエラー メッセージとその原因、および問題を解決するための対策について説明します。</span><span class="sxs-lookup"><span data-stu-id="b811e-106">Provides an explanation of [!INCLUDE[ssDE](../../includes/ssde-md.md)] error messages, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="b811e-107">外部リソース</span><span class="sxs-lookup"><span data-stu-id="b811e-107">External Resources</span></span>  
 <span data-ttu-id="b811e-108">探している情報が製品のドキュメントや Web 上で見つからない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コミュニティで質問したり、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートに問い合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="b811e-108">If you have not found the information you are looking for in the product documentation or on the Web, you can either ask a question in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community or request help from [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="b811e-109">次の表は、リソースへのリンクとその説明を示しています。</span><span class="sxs-lookup"><span data-stu-id="b811e-109">The following table links to and describes these resources.</span></span>  
  
|<span data-ttu-id="b811e-110">リソース</span><span class="sxs-lookup"><span data-stu-id="b811e-110">Resource</span></span>|<span data-ttu-id="b811e-111">説明</span><span class="sxs-lookup"><span data-stu-id="b811e-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="b811e-112">SQL Server コミュニティ</span><span class="sxs-lookup"><span data-stu-id="b811e-112">SQL Server Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42455)|<span data-ttu-id="b811e-113">このサイトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コミュニティが管理するニュースグループおよびフォーラムにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="b811e-113">This site has links to newsgroups and forums monitored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community.</span></span> <span data-ttu-id="b811e-114">ブログや Web サイトなど、コミュニティ情報のソースも一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="b811e-114">It also lists community information sources, such as blogs and Web sites.</span></span> <span data-ttu-id="b811e-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コミュニティは、回答が得られるという保証はありませんが、問題解決に役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="b811e-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] community is very helpful in answering questions, although an answer cannot be guaranteed.</span></span>|  
|[<span data-ttu-id="b811e-116">SQL Server デベロッパー センター コミュニティ</span><span class="sxs-lookup"><span data-stu-id="b811e-116">SQL Server Developer Center Community</span></span>](https://go.microsoft.com/fwlink/?LinkId=42456)|<span data-ttu-id="b811e-117">このサイトは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の開発者にとって役立つニュースグループ、フォーラム、およびその他のコミュニティ リソースに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="b811e-117">This site focuses on the newsgroups, forums, and other community resources that are useful to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] developers.</span></span>|  
|[<span data-ttu-id="b811e-118">Microsoft ヘルプとサポート</span><span class="sxs-lookup"><span data-stu-id="b811e-118">Microsoft Help and Support</span></span>](https://go.microsoft.com/fwlink/?linkid=16419)|<span data-ttu-id="b811e-119">この Web サイトを利用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] のサポート担当者と共にケースを調査できます。</span><span class="sxs-lookup"><span data-stu-id="b811e-119">You can use this Web site to open a case with a [!INCLUDE[msCoName](../../includes/msconame-md.md)] support professional.</span></span>|  
  
  
