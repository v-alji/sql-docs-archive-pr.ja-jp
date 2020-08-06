---
title: オペレーターの可用性の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- reactivating operators
- removing operators
- deleting operators
- available operators [SQL Server]
- dropping operators
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- disabling operators
- operators (users) [Database Engine], changing availability with Management Studio
ms.assetid: 10d58b92-b67b-47e2-af9c-9f9fd6968bba
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb369ea6a2d1edf1ed8f4377b627fb1ba7339a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645351"
---
# <a name="change-an-operator39s-availability"></a><span data-ttu-id="9c078-102">オペレーターの可用性の変更</span><span class="sxs-lookup"><span data-stu-id="9c078-102">Change an Operator&#39;s Availability</span></span>
  <span data-ttu-id="9c078-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、オペレーターの警告通知受信スケジュールを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c078-103">This topic describes how to change an operator's schedule for receiving alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9c078-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9c078-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9c078-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9c078-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9c078-106">Security</span><span class="sxs-lookup"><span data-stu-id="9c078-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9c078-107">**オペレーターが通知を受信できるかどうかを設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="9c078-107">**To change an operator's availability, using:**</span></span>  
  
     [<span data-ttu-id="9c078-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9c078-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9c078-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9c078-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9c078-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="9c078-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9c078-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9c078-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9c078-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="9c078-112">Permissions</span></span>  
 <span data-ttu-id="9c078-113">オペレーターを編集できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="9c078-113">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9c078-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9c078-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="9c078-115">オペレーターが通知を受信できるかどうかを設定するには</span><span class="sxs-lookup"><span data-stu-id="9c078-115">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="9c078-116">**オブジェクト エクスプローラー**で、有効または無効にするオペレーターを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="9c078-116">In **Object Explorer**, click the plus sign to expand server that contains the operator that you want to enable or disable.</span></span>  
  
2.  <span data-ttu-id="9c078-117">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9c078-117">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="9c078-118">プラス記号をクリックして **[オペレーター]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9c078-118">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="9c078-119">有効または無効にするオペレーターを右クリックし、 **[プロパティ]** を選択した後、 **[全般]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c078-119">Right-click the operator that you want to enable or disable and select **Properties**, then click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="9c078-120">[ _Operator_name_の**プロパティ**] ダイアログボックスで、[**有効**] チェックボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="9c078-120">In the _operator_name_**Properties** dialog box, select or clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="9c078-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c078-121">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9c078-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9c078-122">Using Transact-SQL</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="9c078-123">オペレーターが通知を受信できるかどうかを設定するには</span><span class="sxs-lookup"><span data-stu-id="9c078-123">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="9c078-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9c078-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9c078-125">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c078-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9c078-126">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c078-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- disables the 'Fran??ois Ajenstat' operator  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="9c078-127">詳細については、「 [sp_update_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c078-127">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
