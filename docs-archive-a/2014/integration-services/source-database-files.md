---
title: ソースデータベースファイル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31f0c0e0c633ead0c093bdc8e1f20c9b8f23cc28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742342"
---
# <a name="source-database-files"></a><span data-ttu-id="99ab8-102">[転送元のデータベース ファイル]</span><span class="sxs-lookup"><span data-stu-id="99ab8-102">Source database files</span></span>
  <span data-ttu-id="99ab8-103">**[転送元のデータベース ファイル]** ダイアログ ボックスを使用すると、ソース サーバーのデータベース ファイルの名前と場所を表示したり、データベース転送タスクのネットワーク ファイル共有の場所を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="99ab8-103">Use the **Source Database Files** dialog box to view the database file names and locations on the source server, or to specify a network file share location for the Transfer Database task.</span></span> <span data-ttu-id="99ab8-104">このタスクの詳細については、「 [データベース転送タスク](control-flow/transfer-database-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99ab8-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="99ab8-105">このダイアログ ボックスにソース サーバーのデータベース ファイルの名前と場所を入力するには、最初に **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページで **[SourceConnection]** および **[SourceDatabaseName]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="99ab8-105">To populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection** and **SourceDatabaseName** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="99ab8-106">オプション</span><span class="sxs-lookup"><span data-stu-id="99ab8-106">Options</span></span>  
 <span data-ttu-id="99ab8-107">**[転送元ファイル]**</span><span class="sxs-lookup"><span data-stu-id="99ab8-107">**Source File**</span></span>  
 <span data-ttu-id="99ab8-108">転送する対象のソース サーバーのデータベース ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="99ab8-108">Database file names on the source server that will be transferred.</span></span> <span data-ttu-id="99ab8-109">**[転送元ファイル]** は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="99ab8-109">**Source File** is read only.</span></span>  
  
 <span data-ttu-id="99ab8-110">**[同期元フォルダー]**</span><span class="sxs-lookup"><span data-stu-id="99ab8-110">**Source Folder**</span></span>  
 <span data-ttu-id="99ab8-111">転送する対象データベース ファイルが存在する転送元サーバーのフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="99ab8-111">Folder on the source server where the database files to be transferred reside.</span></span> <span data-ttu-id="99ab8-112">**[転送元フォルダー]** は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="99ab8-112">**Source Folder** is read only.</span></span>  
  
 <span data-ttu-id="99ab8-113">**[ネットワーク ファイル共有]**</span><span class="sxs-lookup"><span data-stu-id="99ab8-113">**Network File Share**</span></span>  
 <span data-ttu-id="99ab8-114">データベース ファイルの転送元となるソース サーバーのネットワーク共有フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="99ab8-114">Network shared folder on the source server from where the database files will be transferred.</span></span> <span data-ttu-id="99ab8-115">**[ネットワーク ファイル共有]** は、データベースをオフライン モードで転送する場合に使用します。 **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページの **[Method]** に、 **[DatabaseOffline]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="99ab8-115">Use **Network File Share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="99ab8-116">ネットワーク ファイル共有の場所を入力するか、参照ボタン **([...])** をクリックしてネットワーク ファイル共有の場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="99ab8-116">Enter the network file share location, or click the browse button **(...)** to locate the network file share location.</span></span>  
  
 <span data-ttu-id="99ab8-117">オフライン モードでデータベースを転送すると、データベースは転送先サーバーに転送される前に、転送元サーバーの **[ネットワーク ファイル共有]** の場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="99ab8-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location on the source server before they are transferred to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ab8-118">参照</span><span class="sxs-lookup"><span data-stu-id="99ab8-118">See Also</span></span>  
 <span data-ttu-id="99ab8-119">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="99ab8-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="99ab8-120">[データベース転送タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="99ab8-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="99ab8-121">[データベース転送タスク エディター ([データベース] ページ)](../../2014/integration-services/transfer-database-task-editor-databases-page.md)</span><span class="sxs-lookup"><span data-stu-id="99ab8-121">[Transfer Database Task Editor &#40;Databases Page&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)</span></span>  
  
  
