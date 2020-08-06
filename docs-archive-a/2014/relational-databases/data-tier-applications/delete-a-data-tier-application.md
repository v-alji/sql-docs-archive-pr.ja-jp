---
title: データ層アプリケーションの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deletedacwizard.introduction.f1
- sql12.swb.deletedacwizard.deletedac.f1
- sql12.swb.deletedacwizard.summary.f1
- sql12.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 602256c287a8c7bcf9d3fa5597b2fec2085c626c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736390"
---
# <a name="delete-a-data-tier-application"></a><span data-ttu-id="f537b-102">データ層アプリケーションの削除</span><span class="sxs-lookup"><span data-stu-id="f537b-102">Delete a Data-tier Application</span></span>
  <span data-ttu-id="f537b-103">データ層アプリケーションの削除ウィザードまたは Windows PowerShell スクリプトを使用して、データ層アプリケーションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="f537b-103">You can delete a data-tier application by using either the Delete Data-tier Application wizard or a Windows PowerShell script.</span></span> <span data-ttu-id="f537b-104">関連付けられたデータベースの保持、デタッチ、または削除を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="f537b-104">You can specify whether the associated database is retained, detached, or dropped.</span></span>  
  
-   <span data-ttu-id="f537b-105">**作業を開始する準備:** [制限事項と制約事項](#LimitationsRestrictions)、[権限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="f537b-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="f537b-106">**DAC のアップグレード:** [データ層アプリケーションの登録ウィザードの使用](#UsingDeleteDACWizard)、[PowerShell の使用](#DeleteDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="f537b-106">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="f537b-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="f537b-107">Before You Begin</span></span>  
 <span data-ttu-id="f537b-108">データ層アプリケーション (DAC) インスタンスを削除する場合、3 つのオプションのいずれかを選択して、データ層アプリケーションに関連付けられたデータベースの処理を指定します。</span><span class="sxs-lookup"><span data-stu-id="f537b-108">When you delete a data-tier application (DAC) instance, you choose one of three options specifying what is to be done with the database associated with the data-tier application.</span></span> <span data-ttu-id="f537b-109">どのオプションを選択した場合も、DAC 定義のメタデータが削除されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-109">All three options delete the DAC definition metadata.</span></span> <span data-ttu-id="f537b-110">各オプションは、データ層アプリケーションに関連付けられたデータベースの処理方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="f537b-110">The options differ in what they do with the database associated with the data-tier application.</span></span> <span data-ttu-id="f537b-111">DAC またはデータベースに関連付けられたインスタンスレベルのオブジェクト (ログインなど) が、ウィザードによって削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f537b-111">The wizard does not delete any of the instance-level objects associated with the DAC or database, such as logins.</span></span>  
  
|<span data-ttu-id="f537b-112">オプション</span><span class="sxs-lookup"><span data-stu-id="f537b-112">Option</span></span>|<span data-ttu-id="f537b-113">データベース アクション</span><span class="sxs-lookup"><span data-stu-id="f537b-113">Database actions</span></span>|  
|------------|----------------------|  
|<span data-ttu-id="f537b-114">登録の削除</span><span class="sxs-lookup"><span data-stu-id="f537b-114">Delete registration</span></span>|<span data-ttu-id="f537b-115">関連付けられているデータベースは、そのまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-115">The associated database remains intact.</span></span>|  
|<span data-ttu-id="f537b-116">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="f537b-116">Detach database</span></span>|<span data-ttu-id="f537b-117">関連付けられたデータベースはデタッチされます。</span><span class="sxs-lookup"><span data-stu-id="f537b-117">The associated database is detached.</span></span> <span data-ttu-id="f537b-118">データベース エンジンのインスタンスはデータベースを参照できませんが、データ ファイルとログ ファイルはそのまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-118">The instance of the Database Engine cannot reference the database, but the data and log files are intact.</span></span>|  
|<span data-ttu-id="f537b-119">データベースの削除</span><span class="sxs-lookup"><span data-stu-id="f537b-119">Delete database</span></span>|<span data-ttu-id="f537b-120">関連付けられたデータベースは削除されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-120">The associated database is dropped.</span></span> <span data-ttu-id="f537b-121">データ ファイルとログ ファイルも削除されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-121">The data and log files are deleted.</span></span>|  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="f537b-122">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="f537b-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f537b-123">DAC を削除した後に DAC 定義のメタデータ、またはデータベースを自動的に復元するメカニズムはありません。</span><span class="sxs-lookup"><span data-stu-id="f537b-123">There is no automatic mechanism to restore the DAC definition metadata or the database after you delete a DAC.</span></span> <span data-ttu-id="f537b-124">DAC インスタンスを手動で再構築する方法は、削除オプションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f537b-124">How you can manually rebuild the DAC instance depends on the delete option.</span></span>  
  
|<span data-ttu-id="f537b-125">オプション</span><span class="sxs-lookup"><span data-stu-id="f537b-125">Option</span></span>|<span data-ttu-id="f537b-126">DAC インスタンスの再構築方法</span><span class="sxs-lookup"><span data-stu-id="f537b-126">How to Rebuild the DAC Instance</span></span>|  
|------------|-------------------------------------|  
|<span data-ttu-id="f537b-127">登録の削除</span><span class="sxs-lookup"><span data-stu-id="f537b-127">Delete registration</span></span>|<span data-ttu-id="f537b-128">同じ場所に残っているデータベースから DAC を登録します。</span><span class="sxs-lookup"><span data-stu-id="f537b-128">Register a DAC from the database left in place.</span></span>|  
|<span data-ttu-id="f537b-129">データベースのデタッチ</span><span class="sxs-lookup"><span data-stu-id="f537b-129">Detach database</span></span>|<span data-ttu-id="f537b-130">**sp_attachdb** または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してデータベースを再アタッチして、データベースから新しい DAC インスタンスを登録します。</span><span class="sxs-lookup"><span data-stu-id="f537b-130">Re-attach the database by using **sp_attachdb** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then register a new DAC instance from the database.</span></span>|  
|<span data-ttu-id="f537b-131">データベースの削除</span><span class="sxs-lookup"><span data-stu-id="f537b-131">Delete database</span></span>|<span data-ttu-id="f537b-132">DAC が削除される前に作成された完全バックアップからデータベースを復元して、データベースから新しい DAC インスタンスを登録します。</span><span class="sxs-lookup"><span data-stu-id="f537b-132">Restore the database from a full backup made before the DAC was deleted, and then register a new DAC instance from the database.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="f537b-133">復元または再アタッチされたデータベースから DAC を登録して DAC インスタンスを再構築しても、サーバーの選択ポリシーなど、元の DAC の一部は再作成されません。</span><span class="sxs-lookup"><span data-stu-id="f537b-133">Rebuilding a DAC instance by registering a DAC from a restored or re-attached database will not recreate some parts of the original DAC, such as the server selection policy.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f537b-134">Permissions</span><span class="sxs-lookup"><span data-stu-id="f537b-134">Permissions</span></span>  
 <span data-ttu-id="f537b-135">DAC を削除できるのは、 **sysadmin** または **serveradmin** 固定サーバー ロールのメンバーか、データベース所有者のみです。</span><span class="sxs-lookup"><span data-stu-id="f537b-135">A DAC can only be deleted by members of the **sysadmin** or **serveradmin** fixed server roles, or by the database owner.</span></span> <span data-ttu-id="f537b-136">あらかじめ登録された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウント ( **sa** ) もこのウィザードを起動できます。</span><span class="sxs-lookup"><span data-stu-id="f537b-136">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also launch the wizard.</span></span>  
  
##  <a name="using-the-delete-data-tier-application-wizard"></a><a name="UsingDeleteDACWizard"></a> <span data-ttu-id="f537b-137">データ層アプリケーションの削除ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="f537b-137">Using the Delete Data-tier Application Wizard</span></span>  
 <span data-ttu-id="f537b-138">**ウィザードを使用して DAC を削除するには**</span><span class="sxs-lookup"><span data-stu-id="f537b-138">**To Delete a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="f537b-139">**オブジェクト エクスプローラー**で、削除する DAC を含んだインスタンスのノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f537b-139">In **Object Explorer**, expand the node for the instance containing the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="f537b-140">**[管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f537b-140">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="f537b-141">**[データ層アプリケーション]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f537b-141">Expand the **Data-tier Applications** node.</span></span>  
  
4.  <span data-ttu-id="f537b-142">削除する DAC を右クリックし、 **[データ層アプリケーションの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f537b-142">Right-click the DAC to be deleted, and then select **Delete Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="f537b-143">ウィザードの各ダイアログの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f537b-143">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="f537b-144">はじめに</span><span class="sxs-lookup"><span data-stu-id="f537b-144">Introduction</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="f537b-145">方法の選択</span><span class="sxs-lookup"><span data-stu-id="f537b-145">Choose Method</span></span>](#Choose_method)  
  
    3.  [<span data-ttu-id="f537b-146">まとめ</span><span class="sxs-lookup"><span data-stu-id="f537b-146">Summary</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="f537b-147">データ層アプリケーションの削除</span><span class="sxs-lookup"><span data-stu-id="f537b-147">Delete Data-tier Application</span></span>](#Delete_datatier_application)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="f537b-148">[説明] ページ</span><span class="sxs-lookup"><span data-stu-id="f537b-148">Introduction Page</span></span>  
 <span data-ttu-id="f537b-149">このページでは、データ層アプリケーションを削除する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="f537b-149">This page describes the steps for deleting a data-tier application.</span></span>  
  
 <span data-ttu-id="f537b-150">**[次回からこのページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="f537b-150">**Do not show this page again.**</span></span> <span data-ttu-id="f537b-151">: 今後このページを表示しないようにするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f537b-151">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="f537b-152">**[次へ >]** : **[方法の選択]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="f537b-152">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="f537b-153">**[キャンセル]** : データ層アプリケーションもデータベースも削除することなくウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f537b-153">**Cancel** - Ends the wizard without deleting a data-tier application or database.</span></span>  
  
##  <a name="choose-method-page"></a><a name="Choose_method"></a> <span data-ttu-id="f537b-154">[方法の選択] ページ</span><span class="sxs-lookup"><span data-stu-id="f537b-154">Choose Method Page</span></span>  
 <span data-ttu-id="f537b-155">削除する DAC に関連付けられているデータベースの処理オプションを指定するには、このページを使用します。</span><span class="sxs-lookup"><span data-stu-id="f537b-155">Use this page to specify the option for handling the database associated with the DAC to be deleted.</span></span>  
  
 <span data-ttu-id="f537b-156">**[登録の削除]** : データ層アプリケーションを定義しているメタデータを削除しますが、関連付けられたデータベースはそのまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-156">**Delete registration** - Removes the metadata defining the data-tier application, but leaves the associated database intact.</span></span>  
  
 <span data-ttu-id="f537b-157">**[データベースのデタッチ]** : データ層アプリケーションを定義しているメタデータを削除して、関連付けられたデータベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="f537b-157">**Detach database** - Removes the metadata defining the data-tier application and detaches the associated database.</span></span>  
  
 <span data-ttu-id="f537b-158">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスはデータベースを参照できなくなりますが、データ ファイルとログ ファイルはそのまま保持されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-158">The database can no longer be referenced by that instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but the data and log files remain intact.</span></span>  
  
 <span data-ttu-id="f537b-159">**[データベースの削除]** : DAC を定義しているメタデータと、関連付けられたデータベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="f537b-159">**Delete database** - Removes the metadata defining the DAC and drops the associated database.</span></span>  
  
 <span data-ttu-id="f537b-160">データベースのデータ ファイルとログ ファイルは、完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-160">The data and log files for the database are permanently deleted.</span></span>  
  
 <span data-ttu-id="f537b-161">\*\* \< Previous\*\* -[**概要**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f537b-161">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="f537b-162">**[次へ]** : **[概要]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="f537b-162">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="f537b-163">**[キャンセル]** : DAC もデータベースも削除することなくウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f537b-163">**Cancel** - Ends the wizard without deleting the DAC or database.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="f537b-164">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="f537b-164">Summary Page</span></span>  
 <span data-ttu-id="f537b-165">このページでは、DAC インスタンスの削除時にウィザードが行うアクションを確認します。</span><span class="sxs-lookup"><span data-stu-id="f537b-165">Use this page to review the actions the wizard will take when deleting the DAC instance.</span></span>  
  
 <span data-ttu-id="f537b-166">**[選択内容の概要の確認]** : ボックスに表示されている DAC、データベース、および削除方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="f537b-166">**Review your selection summary** - Review the DAC, database, and deletion method displayed in the box.</span></span> <span data-ttu-id="f537b-167">情報が正しい場合は、 **[次へ]** または **[完了]** をクリックして DAC を削除します。</span><span class="sxs-lookup"><span data-stu-id="f537b-167">If the information is correct, select either **Next** or **Finish** to delete the DAC.</span></span> <span data-ttu-id="f537b-168">DAC とデータベースの情報が正しくない場合は、 **[キャンセル]** をクリックしてから正しい DAC を選択します。</span><span class="sxs-lookup"><span data-stu-id="f537b-168">If the DAC and database information is not correct, select **Cancel** and select the correct DAC.</span></span> <span data-ttu-id="f537b-169">削除方法が正しくない場合は、 **[戻る]** をクリックして **[方法の選択]** ページに戻り、別の方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="f537b-169">If the deletion method is not correct, select **Previous** to return to the **Choose Method** page and select a different method.</span></span>  
  
 <span data-ttu-id="f537b-170">\*\* \< Previous\*\* -別の削除方法を選択するには、 **[メソッドの選択**] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f537b-170">**\< Previous** - Returns to the **Choose Method** page to choose a different delete method.</span></span>  
  
 <span data-ttu-id="f537b-171">**[次へ >]**: 前のページで選択した方法で DAC インスタンスを削除して、**[データ層アプリケーションの削除]** ページに進みます。</span><span class="sxs-lookup"><span data-stu-id="f537b-171">**Next >** - Deletes the DAC instance using the method you chose on the previous page, and proceeds to the **Delete Data-tier Application** page.</span></span>  
  
 <span data-ttu-id="f537b-172">**[キャンセル]** : DAC インスタンスを削除することなくウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f537b-172">**Cancel** - Ends the wizard without deleting the DAC instance.</span></span>  
  
##  <a name="delete-data-tier-application-page"></a><a name="Delete_datatier_application"></a><span data-ttu-id="f537b-173">[データ層アプリケーションの削除] ページ</span><span class="sxs-lookup"><span data-stu-id="f537b-173">Delete Data-tier Application Page</span></span>  
 <span data-ttu-id="f537b-174">このページには、削除操作の成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-174">This page reports the success or failure of the delete operation.</span></span>  
  
 <span data-ttu-id="f537b-175">**[DAC の削除]** : DAC インスタンスを削除するために行った各アクションの成功または失敗が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-175">**Deleting the DAC** - Reports the success or failure of each action taken to delete the DAC instance.</span></span> <span data-ttu-id="f537b-176">内容を確認して、各アクションの成功または失敗を判断します。</span><span class="sxs-lookup"><span data-stu-id="f537b-176">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="f537b-177">エラーが発生したアクションには、 **[結果]** 列にリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-177">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="f537b-178">そのアクションのエラーのレポートを表示するには、リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f537b-178">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="f537b-179">**[レポートの保存]** : 削除レポートを HTML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="f537b-179">**Save Report** - Select this button to save the deletion report to an HTML file.</span></span> <span data-ttu-id="f537b-180">ファイルには、アクションで発生したすべてのエラーを含む、各アクションのステータスが報告されます。</span><span class="sxs-lookup"><span data-stu-id="f537b-180">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="f537b-181">既定のフォルダーは、Windows アカウントの Documents フォルダーにある SQL Server Management Studio\DAC Packages フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="f537b-181">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account..</span></span>  
  
 <span data-ttu-id="f537b-182">**[完了]** : ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="f537b-182">**Finish** - Ends the wizard.</span></span>  
  
##  <a name="delete-a-dac-using-powershell"></a><a name="DeleteDACPowerShell"></a><span data-ttu-id="f537b-183">PowerShell を使用して DAC を削除する</span><span class="sxs-lookup"><span data-stu-id="f537b-183">Delete a DAC Using PowerShell</span></span>  
 <span data-ttu-id="f537b-184">**PowerShell スクリプトを使用して DAC を削除するには**</span><span class="sxs-lookup"><span data-stu-id="f537b-184">**To delete a DAC using a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="f537b-185">SMO サーバー オブジェクトを作成し、削除する DAC を含んだインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="f537b-185">Create a SMO Server object and set it to the instance that contains the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="f537b-186">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f537b-186">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="f537b-187">`add_DacActionStarted` および `add_DacActionFinished` を使用して、DAC アップグレード イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="f537b-187">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
4.  <span data-ttu-id="f537b-188">削除する DAC を指定します。</span><span class="sxs-lookup"><span data-stu-id="f537b-188">Specify the DAC to delete.</span></span>  
  
5.  <span data-ttu-id="f537b-189">どの削除オプションが適しているかによって、これらの 3 つのコードのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="f537b-189">Use one of these three sets of code, depending on which delete option is appropriate:</span></span>  
  
    -   <span data-ttu-id="f537b-190">DAC 登録を削除し、データベースをそのままにするには、`Unmanage()` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f537b-190">To delete the DAC registration but leave the database intact, use the `Unmanage()` method.</span></span>  
  
    -   <span data-ttu-id="f537b-191">DAC 登録を削除し、データベースをデタッチするには、`Uninstall()` メソッドを使用し、`DetachDatabase` を指定します。</span><span class="sxs-lookup"><span data-stu-id="f537b-191">To delete the DAC registration and detach the database, use the `Uninstall()` method and specify `DetachDatabase`.</span></span>  
  
    -   <span data-ttu-id="f537b-192">DAC 登録を削除し、データベースを削除するには、`Uninstall()` メソッドを使用し、`DropDatabase` を指定します。</span><span class="sxs-lookup"><span data-stu-id="f537b-192">To delete the DAC registration and drop the database, use the `Uninstall()` method and specify `DropDatabase`.</span></span>  
  
### <a name="example-deleting-the-dac-but-leaving-the-database-powershell"></a><span data-ttu-id="f537b-193">DAC のみ削除してデータベースはそのまま残す例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f537b-193">Example Deleting the DAC but Leaving the Database (PowerShell)</span></span>  
 <span data-ttu-id="f537b-194">次の例では、MyApplication という DAC を削除します。`Unmanage()` メソッドを使用して DAC のみ削除し、データベースはそのままにします。</span><span class="sxs-lookup"><span data-stu-id="f537b-194">The following example deletes a DAC named MyApplication using the `Unmanage()` method to delete the DAC but leave the database intact.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacstore.Unmanage($dacName)  
```  
  
### <a name="example-deleting-the-dac-and-detaching-the-database-powershell"></a><span data-ttu-id="f537b-195">DAC を削除してデータベースをデタッチする例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f537b-195">Example Deleting the DAC and Detaching the Database (PowerShell)</span></span>  
 <span data-ttu-id="f537b-196">次の例では、MyApplication という DAC を削除します。`Uninstall()` メソッドを使用して DAC を削除し、データベースをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="f537b-196">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and detach the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```  
  
### <a name="example-deleting-the-dac-and-dropping-the-database-powershell"></a><span data-ttu-id="f537b-197">DAC を削除してデータベースを削除する例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f537b-197">Example Deleting the DAC and Dropping the Database (PowerShell)</span></span>  
 <span data-ttu-id="f537b-198">次の例では、MyApplication という DAC を削除します。`Uninstall()` メソッドを使用して DAC を削除し、データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="f537b-198">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and drop the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and drop the associated database.  
## $dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```  
  
## <a name="see-also"></a><span data-ttu-id="f537b-199">参照</span><span class="sxs-lookup"><span data-stu-id="f537b-199">See Also</span></span>  
 <span data-ttu-id="f537b-200">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="f537b-200">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="f537b-201">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="f537b-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="f537b-202">[データ層アプリケーションの配置](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="f537b-202">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="f537b-203">[データベースを DAC として登録する](register-a-database-as-a-dac.md) </span><span class="sxs-lookup"><span data-stu-id="f537b-203">[Register a Database As a DAC](register-a-database-as-a-dac.md) </span></span>  
 <span data-ttu-id="f537b-204">[SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f537b-204">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="f537b-205">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f537b-205">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
