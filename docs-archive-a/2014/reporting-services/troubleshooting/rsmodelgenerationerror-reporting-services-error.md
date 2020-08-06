---
title: rsModelGenerationError - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 713de57f0f2957983966f8ef0345bb374c311781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641420"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a><span data-ttu-id="b947f-102">rsModelGenerationError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="b947f-102">rsModelGenerationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="b947f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="b947f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b947f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="b947f-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="b947f-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b947f-105">Event ID</span></span>|<span data-ttu-id="b947f-106">rsRenderingError</span><span class="sxs-lookup"><span data-stu-id="b947f-106">rsRenderingError</span></span>|  
|<span data-ttu-id="b947f-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="b947f-107">Event Source</span></span>|<span data-ttu-id="b947f-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="b947f-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="b947f-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b947f-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="b947f-110">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="b947f-110">Message Text</span></span>|<span data-ttu-id="b947f-111">モデルの生成中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b947f-111">An error occurred while generating model.</span></span> <span data-ttu-id="b947f-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span><span class="sxs-lookup"><span data-stu-id="b947f-112">(rsModelGenerationError) (ReportingServicesLibrary) %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b947f-113">説明</span><span class="sxs-lookup"><span data-stu-id="b947f-113">Explanation</span></span>  
 <span data-ttu-id="b947f-114">レポート モデルを生成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="b947f-114">The report model could not be generated.</span></span> <span data-ttu-id="b947f-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 以前のバージョンでは、このエラーは、System.Data.DataSet オブジェクトでデータベース スキーマ内のテーブルまたはリレーションシップを処理できない場合に表示される可能性があります。たとえば、1 つのテーブル内の同じ列に 2 つの外部キーが定義されている場合などです。</span><span class="sxs-lookup"><span data-stu-id="b947f-115">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 and earlier versions, this error is most likely displayed when the System.Data.DataSet object cannot handle a table or relationship within the database schema, such as when, for example, two foreign keys are defined on the same column within a table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b947f-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="b947f-116">User Action</span></span>  
 <span data-ttu-id="b947f-117">このメッセージが表示される原因となった具体的な理由を特定するには、\Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles にあるレポート サーバーのログ ファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="b947f-117">To determine the specific reason that caused this message to appear, review the report server log files, which are located at \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="b947f-118">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="b947f-118">Internal-Only</span></span>  
  
