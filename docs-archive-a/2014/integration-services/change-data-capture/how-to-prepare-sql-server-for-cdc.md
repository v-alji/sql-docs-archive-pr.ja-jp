---
title: CDC 用に SQL Server を準備する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a327fa18-58f4-4e69-bb87-44faf47e20ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbd285faaa55a28ad82beb673fa783570809bd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710986"
---
# <a name="how-to-prepare-sql-server-for-cdc"></a><span data-ttu-id="9a829-102">CDC 用に SQL Server を準備する方法</span><span class="sxs-lookup"><span data-stu-id="9a829-102">How to Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="9a829-103">Oracle CDC サービスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのターゲット インスタンスに MSXDBCDC データベースが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a829-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="9a829-104">このデータベースを作成するには、CDC Service 構成コンソールの "SQL Server の準備" アクションを使用します。このタスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各ターゲット インスタンスに対して一度だけ実行します。</span><span class="sxs-lookup"><span data-stu-id="9a829-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="9a829-105">次に、CDC Service 構成コンソールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを Oracle Change Data Capture 用に準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a829-105">The following describes how to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for Oracle Change Data Capture using the CDC Service Configuration Console.</span></span> <span data-ttu-id="9a829-106">このプロセスによって、MSXDBCDC データベースが作成され、必要なテーブル、ストアド プロシージャ、およびその他のアーティファクトが定義されます。</span><span class="sxs-lookup"><span data-stu-id="9a829-106">This process creates the MSXDBCDC database and defines the required tables, stored procedures, and other required artifacts.</span></span>  
  
 <span data-ttu-id="9a829-107">Oracle CDC 用の SQL Server の準備は、Oracle CDC Service の管理者が実行します。</span><span class="sxs-lookup"><span data-stu-id="9a829-107">Preparing the SQL Server for Oracle CDC is done by the Oracle CDC Service Administrator.</span></span> <span data-ttu-id="9a829-108">CDC Service の管理者ロールの詳細については、「 [Change Data Capture Service for Oracle のユーザーロール](user-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a829-108">For more information about the CDC Service Administrator role, see [User Roles for Change Data Capture Service for Oracle by Attunity](user-roles.md).</span></span>  
  
### <a name="to-enable-sql-server-for-cdc"></a><span data-ttu-id="9a829-109">CDC 用に SQL Server を有効にするには</span><span class="sxs-lookup"><span data-stu-id="9a829-109">To enable SQL Server for CDC</span></span>  
  
1.  <span data-ttu-id="9a829-110">**[スタート]** メニューの **[CDC Service Configuration for Oracle]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a829-110">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="9a829-111">左ペインで **[ローカルの CDC Service]** を選択してから、 **[アクション]** ペインの **[SQL Server の準備]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a829-111">From the left pane, select **Local CDC Services** then from the **Actions** pane, click **Prepare SQL Server**.</span></span>  
  
     <span data-ttu-id="9a829-112">**[ローカルの CDC Service]** を右クリックして **[SQLServer の準備]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9a829-112">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
3.  <span data-ttu-id="9a829-113">[Oracle CDC 用 SQL Server インスタンスの準備] ダイアログ ボックスに必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="9a829-113">Enter the required information in the Preparing SQL Server Instance for Oracle CDC dialog box.</span></span> <span data-ttu-id="9a829-114">このダイアログ ボックスに必要な情報を入力する方法については、「 [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a829-114">For information on how to enter the required information into this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span>  
  
     <span data-ttu-id="9a829-115">Oracle CDC 用に SQL Server インスタンスを準備するには、ログインが MSXDBCDC データベースに対する書き込み権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a829-115">To Prepare the SQL Server instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="9a829-116">`sysasmin` ロールのメンバーなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="9a829-116">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
 <span data-ttu-id="9a829-117">**注**: **[スクリプトの表示]** をクリックすると、セットアップ スクリプトの読み取り専用バージョンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9a829-117">**Note**: You can click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="9a829-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム管理者は、必要に応じて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理コンソールにこのスクリプトをコピーして編集および実行することができます。</span><span class="sxs-lookup"><span data-stu-id="9a829-118">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Console to edit and execute it, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a829-119">参照</span><span class="sxs-lookup"><span data-stu-id="9a829-119">See Also</span></span>  
 [<span data-ttu-id="9a829-120">CDC 用の SQL Server の準備</span><span class="sxs-lookup"><span data-stu-id="9a829-120">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
