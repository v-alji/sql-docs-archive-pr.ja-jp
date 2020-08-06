---
title: 転送先データベースファイル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d0ab2c0ff39fc728afc17b59f0d4bae076e4022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644570"
---
# <a name="destination-database-files"></a><span data-ttu-id="d5e29-102">[転送先データベース ファイル]</span><span class="sxs-lookup"><span data-stu-id="d5e29-102">Destination Database Files</span></span>
  <span data-ttu-id="d5e29-103">**[転送先データベース ファイル]** ダイアログ ボックスを使用すると、転送先サーバーのデータベース ファイルの名前と場所を表示または変更したり、データベース転送タスクのネットワーク ファイルの場所を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="d5e29-103">Use the **Destination Database Files** dialog box to view or change the database file names and locations on the destination server, or to specify a network file location for the Transfer Database task.</span></span> <span data-ttu-id="d5e29-104">このタスクの詳細については、「 [データベース転送タスク](control-flow/transfer-database-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5e29-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="d5e29-105">このダイアログ ボックスで転送元サーバーのデータベース ファイルの名前と場所を自動的に入力するには、最初に **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページで、 **[SourceConnection]** 、 **[SourceDatabaseName]** 、および **[SourceDatabaseFiles]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5e29-105">To automatically populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d5e29-106">オプション</span><span class="sxs-lookup"><span data-stu-id="d5e29-106">Options</span></span>  
 <span data-ttu-id="d5e29-107">**[転送先ファイル]**</span><span class="sxs-lookup"><span data-stu-id="d5e29-107">**Destination File**</span></span>  
 <span data-ttu-id="d5e29-108">転送先サーバーの転送されたデータベース ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="d5e29-108">Names of the transferred database files on the destination server.</span></span>  
  
 <span data-ttu-id="d5e29-109">ファイル名を入力するか、ファイル名をクリックして編集します。</span><span class="sxs-lookup"><span data-stu-id="d5e29-109">Enter the file name, or click the file name to edit it.</span></span>  
  
 <span data-ttu-id="d5e29-110">**[同期先フォルダー]**</span><span class="sxs-lookup"><span data-stu-id="d5e29-110">**Destination Folder**</span></span>  
 <span data-ttu-id="d5e29-111">データベース ファイルの転送先となる転送先サーバーのフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="d5e29-111">Folder on the destination server where the database files will be transferred to.</span></span>  
  
 <span data-ttu-id="d5e29-112">フォルダー パスを入力するか、フォルダー パスをクリックして編集するか、参照ボタンをクリックしてデータベース ファイルを転送する転送先サーバーのフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5e29-112">Enter the folder path, click the folder path to edit it, or click browse to locate the folder where you want to transfer the database files on the destination server.</span></span>  
  
 <span data-ttu-id="d5e29-113">**[ネットワーク ファイル共有]**</span><span class="sxs-lookup"><span data-stu-id="d5e29-113">**Network File Share**</span></span>  
 <span data-ttu-id="d5e29-114">データベース ファイルの転送先となる転送先サーバーのネットワーク共有フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="d5e29-114">Network shared folder on the destination server where the database files will be transferred to.</span></span> <span data-ttu-id="d5e29-115">**[ネットワーク ファイル共有]** は、データベースをオフライン モードで転送する場合に使用します。 **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページの **[Method]** に、 **[DatabaseOffline]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5e29-115">Use **Network file share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="d5e29-116">ネットワーク ファイル共有の場所を入力するか、参照ボタンをクリックしてネットワーク ファイル共有の場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="d5e29-116">Enter the network file share location, or click browse to locate the network file share location.</span></span>  
  
 <span data-ttu-id="d5e29-117">オフライン モードでデータベースを転送すると、データベース ファイルは **[転送先フォルダー]** で指定した場所に転送される前に、 **[ネットワーク ファイル共有]** で指定した場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d5e29-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location before they are transferred to the **Destination folder** location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e29-118">参照</span><span class="sxs-lookup"><span data-stu-id="d5e29-118">See Also</span></span>  
 <span data-ttu-id="d5e29-119">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d5e29-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d5e29-120">[データベース転送タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d5e29-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d5e29-121">[データベース転送タスク エディター ([データベース] ページ)](../../2014/integration-services/transfer-database-task-editor-databases-page.md)</span><span class="sxs-lookup"><span data-stu-id="d5e29-121">[Transfer Database Task Editor &#40;Databases Page&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)</span></span>  
  
  
