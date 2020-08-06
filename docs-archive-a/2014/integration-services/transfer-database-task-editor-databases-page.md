---
title: '[データベース転送タスクエディター] ([データベース] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.database.f1
helpviewer_keywords:
- Transfer Database Task Editor
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df4452e28a32463a7825e9c64cfd053f98c53ee8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710962"
---
# <a name="transfer-database-task-editor-databases-page"></a><span data-ttu-id="15ead-102">[データベース転送タスク エディター] ([データベース] ページ)</span><span class="sxs-lookup"><span data-stu-id="15ead-102">Transfer Database Task Editor (Databases Page)</span></span>
  <span data-ttu-id="15ead-103">**[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページを使用すると、データベース転送タスクに使用される転送元および転送先のデータベースのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="15ead-103">Use the **Databases** page of the **Transfer Database Task Editor** dialog box to specify properties for the source and destination databases involved in the Transfer Database task.</span></span> <span data-ttu-id="15ead-104">データベース転送タスクは、2 つの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの間で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベースをコピーまたは移動します。</span><span class="sxs-lookup"><span data-stu-id="15ead-104">The Transfer Database task copies or moves a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15ead-105">このタスクを使用して、同じサーバー内でデータベースをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="15ead-105">This task can also be used to copy a database within the same server.</span></span> <span data-ttu-id="15ead-106">このタスクの詳細については、「 [データベース転送タスク](control-flow/transfer-database-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15ead-106">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="15ead-107">オプション</span><span class="sxs-lookup"><span data-stu-id="15ead-107">Options</span></span>  
 <span data-ttu-id="15ead-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="15ead-108">**SourceConnection**</span></span>  
 <span data-ttu-id="15ead-109">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="15ead-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="15ead-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="15ead-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="15ead-111">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="15ead-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="15ead-112">**[DestinationDatabaseName]**</span><span class="sxs-lookup"><span data-stu-id="15ead-112">**DestinationDatabaseName**</span></span>  
 <span data-ttu-id="15ead-113">転送先サーバーの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-113">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database on the destination server.</span></span>  
  
 <span data-ttu-id="15ead-114">このフィールドにソース データベースの名前を自動的に入力するには、 **[SourceConnection]** と **[SourceDatabaseName]** を先に指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-114">To automatically populate this field with the source database name, specify the **SourceConnection** and **SourceDatabaseName** first.</span></span>  
  
 <span data-ttu-id="15ead-115">転送先サーバー上のデータベースの名前を変更するには、このフィールドに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="15ead-115">To rename the database on the destination server, type the new name in this field.</span></span>  
  
 <span data-ttu-id="15ead-116">**[DestinationDatabaseFiles]**</span><span class="sxs-lookup"><span data-stu-id="15ead-116">**DestinationDatabaseFiles**</span></span>  
 <span data-ttu-id="15ead-117">転送先サーバーにおけるデータベース ファイルの名前と場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-117">Specifies the names and locations of the database files on the destination server.</span></span>  
  
 <span data-ttu-id="15ead-118">このフィールドにソース データベース ファイルの名前と場所を自動的に入力するには、 **[SourceConnection]** 、 **[SourceDatabaseName]** 、 **[SourceDatabaseFiles]** を先に指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-118">To automatically populate this field with the source database file names and locations, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first.</span></span>  
  
 <span data-ttu-id="15ead-119">データベース ファイルの名前を変更するか、転送先サーバー上の新しい場所を指定するには、このフィールドにソース データベースの情報を入力した後、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ead-119">To rename the database files or to specify the new locations on the destination server, populate this field with the source database information, and then click the browse button.</span></span> <span data-ttu-id="15ead-120">**[転送先データベース ファイル]** ダイアログ ボックスで、 **[転送先ファイル]** 、 **[転送先フォルダー]** 、または **[ネットワーク ファイル共有]** を編集します。</span><span class="sxs-lookup"><span data-stu-id="15ead-120">In the **Destination database files** dialog box, edit the **Destination File**, **Destination Folder**, or **Network File Share**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15ead-121">参照ボタンを使用してデータベース ファイルを指定した場合、ファイルの場所はローカル ドライブの表記 (c:\\など) を使用して入力されます。</span><span class="sxs-lookup"><span data-stu-id="15ead-121">If you locate the database files by using the browse button, the file location is entered using the local drive notation: for example, c:\\.</span></span> <span data-ttu-id="15ead-122">これをコンピューター名と共有名を含むネットワーク共有の表記に変える必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ead-122">You must replace this with the network share notation, including the computer name and share name.</span></span> <span data-ttu-id="15ead-123">既定の管理共有を使用する場合、$ 表記を使用し、その共有に対する管理アクセスを行える必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ead-123">If the default administrative share is used, you must use the $ notation, and have administrative access to the share.</span></span>  
  
 <span data-ttu-id="15ead-124">**[DestinationOverwrite]**</span><span class="sxs-lookup"><span data-stu-id="15ead-124">**DestinationOverwrite**</span></span>  
 <span data-ttu-id="15ead-125">転送先サーバーのデータベースを上書きできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-125">Specify whether the database on the destination server can be overwritten.</span></span>  
  
 <span data-ttu-id="15ead-126">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="15ead-126">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="15ead-127">値</span><span class="sxs-lookup"><span data-stu-id="15ead-127">Value</span></span>|<span data-ttu-id="15ead-128">説明</span><span class="sxs-lookup"><span data-stu-id="15ead-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15ead-129">**True** にします</span><span class="sxs-lookup"><span data-stu-id="15ead-129">**True**</span></span>|<span data-ttu-id="15ead-130">転送先サーバーのデータベースを上書きします。</span><span class="sxs-lookup"><span data-stu-id="15ead-130">Overwrite destination server database.</span></span>|  
|<span data-ttu-id="15ead-131">**False**</span><span class="sxs-lookup"><span data-stu-id="15ead-131">**False**</span></span>|<span data-ttu-id="15ead-132">転送先サーバーのデータベースを上書きしません。</span><span class="sxs-lookup"><span data-stu-id="15ead-132">Do not overwrite destination server database.</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="15ead-133">**[DestinationOverwrite]** に **[True]** を指定した場合、転送先サーバーのデータベースのデータが上書きされます。これにより、データが失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15ead-133">The data in the destination server database will be overwritten if you specify **True** for **DestinationOverwrite**, which may result in data loss.</span></span> <span data-ttu-id="15ead-134">データが失われないようにするには、データベース転送タスクを実行する前に、転送先サーバーのデータベースを別の場所にバックアップしておきます。</span><span class="sxs-lookup"><span data-stu-id="15ead-134">To avoid this, back up the destination server database to another location before executing the Transfer Database task.</span></span>  
  
 <span data-ttu-id="15ead-135">**操作**</span><span class="sxs-lookup"><span data-stu-id="15ead-135">**Action**</span></span>  
 <span data-ttu-id="15ead-136">タスクによってデータベースを転送先サーバーにコピー ( **[Copy]** ) するのか移動 ( **[Move]** ) するのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-136">Specify whether the task will **Copy** or **Move** the database to the destination server.</span></span>  
  
 <span data-ttu-id="15ead-137">**方法**</span><span class="sxs-lookup"><span data-stu-id="15ead-137">**Method**</span></span>  
 <span data-ttu-id="15ead-138">転送元サーバーのデータベースがオンライン モードのときにタスクを実行するか、オフライン モードのときに実行するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-138">Specify whether the task will be executed while the database on the source server is in online or offline mode.</span></span>  
  
 <span data-ttu-id="15ead-139">オフライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ead-139">To transfer a database using offline mode, the user that runs the package must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="15ead-140">オンライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが **sysadmin** 固定サーバー ロールのメンバーであるか、選択されたデータベースのデータベース所有者 (**dbo**) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ead-140">To transfer a database using the online mode, the user that runs the package must be a member of the **sysadmin** fixed server role, or the database owner (**dbo**) of the selected database.</span></span>  
  
 <span data-ttu-id="15ead-141">**[SourceDatabaseName]**</span><span class="sxs-lookup"><span data-stu-id="15ead-141">**SourceDatabaseName**</span></span>  
 <span data-ttu-id="15ead-142">コピーまたは移動されるデータベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="15ead-142">Select the name of the database to be copied or moved.</span></span>  
  
 <span data-ttu-id="15ead-143">**[SourceDatabaseFiles]**</span><span class="sxs-lookup"><span data-stu-id="15ead-143">**SourceDatabaseFiles**</span></span>  
 <span data-ttu-id="15ead-144">参照ボタンをクリックして、データベース ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="15ead-144">Click the browse button to select the database files.</span></span>  
  
 <span data-ttu-id="15ead-145">**[ReattachSourceDatabase]**</span><span class="sxs-lookup"><span data-stu-id="15ead-145">**ReattachSourceDatabase**</span></span>  
 <span data-ttu-id="15ead-146">失敗した場合に、ソース データベースの再アタッチを試行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15ead-146">Specify whether the task will attempt to reattach the source database if a failure occurs.</span></span>  
  
 <span data-ttu-id="15ead-147">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="15ead-147">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="15ead-148">値</span><span class="sxs-lookup"><span data-stu-id="15ead-148">Value</span></span>|<span data-ttu-id="15ead-149">説明</span><span class="sxs-lookup"><span data-stu-id="15ead-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15ead-150">**True** にします</span><span class="sxs-lookup"><span data-stu-id="15ead-150">**True**</span></span>|<span data-ttu-id="15ead-151">ソース データベースを再アタッチします。</span><span class="sxs-lookup"><span data-stu-id="15ead-151">Reattach source database.</span></span>|  
|<span data-ttu-id="15ead-152">**False**</span><span class="sxs-lookup"><span data-stu-id="15ead-152">**False**</span></span>|<span data-ttu-id="15ead-153">ソース データベースを再アタッチしません。</span><span class="sxs-lookup"><span data-stu-id="15ead-153">Do not reattach source database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15ead-154">参照</span><span class="sxs-lookup"><span data-stu-id="15ead-154">See Also</span></span>  
 <span data-ttu-id="15ead-155">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="15ead-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="15ead-156">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="15ead-156">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="15ead-157">[データベース転送タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="15ead-157">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="15ead-158">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="15ead-158">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="15ead-159">SMO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="15ead-159">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
