---
title: '[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d4e582558a1f86b18d935fcc6235ba5839faa031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642882"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="feac6-102">[SSIS パッケージの保存]\(SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="feac6-102">Save SSIS Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="feac6-103">[ **SSIS パッケージの保存**] ページを使用すると、Integration Services () パッケージの名前を指定し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` データベースまたは拡張子が .dtsx のファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="feac6-103">Use the **Save SSIS Package** page to name, describe, and save a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database or to a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="feac6-104">では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ウィザードによって作成されたパッケージを保存するオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="feac6-104">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="feac6-105">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feac6-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="feac6-106">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feac6-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="feac6-107">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="feac6-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="feac6-108">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="feac6-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="feac6-109">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="feac6-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="feac6-110">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="feac6-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="feac6-111">静的オプション</span><span class="sxs-lookup"><span data-stu-id="feac6-111">Static Options</span></span>  
 <span data-ttu-id="feac6-112">**名前**</span><span class="sxs-lookup"><span data-stu-id="feac6-112">**Name**</span></span>  
 <span data-ttu-id="feac6-113">パッケージの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="feac6-113">Provide a unique name for the package.</span></span>  
  
 <span data-ttu-id="feac6-114">**説明**</span><span class="sxs-lookup"><span data-stu-id="feac6-114">**Description**</span></span>  
 <span data-ttu-id="feac6-115">パッケージの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="feac6-115">Provide a description for the package.</span></span> <span data-ttu-id="feac6-116">パッケージを自己文書化して目的を明確にし、保守が容易になるように、パッケージの目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="feac6-116">As a best practice, describe the package in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="feac6-117">**移行先**</span><span class="sxs-lookup"><span data-stu-id="feac6-117">**Target**</span></span>  
 <span data-ttu-id="feac6-118">保存先ファイルとしてあらかじめ指定されているターゲット ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはファイル) を表示します。</span><span class="sxs-lookup"><span data-stu-id="feac6-118">View the target ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or file) that was previously specified for the destination file.</span></span>  
  
## <a name="target-dynamic-options"></a><span data-ttu-id="feac6-119">保存先の動的オプション</span><span class="sxs-lookup"><span data-stu-id="feac6-119">Target Dynamic Options</span></span>  
  
### <a name="target--sql-server"></a><span data-ttu-id="feac6-120">[変換先] = [SQL Server]</span><span class="sxs-lookup"><span data-stu-id="feac6-120">Target = SQL Server</span></span>  
 <span data-ttu-id="feac6-121">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="feac6-121">**Server name**</span></span>  
 <span data-ttu-id="feac6-122">保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、保存先のサーバー名を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="feac6-122">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, type or select the destination server name.</span></span>  
  
 <span data-ttu-id="feac6-123">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="feac6-123">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="feac6-124">保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、Windows 統合認証を使用してサーバーに接続するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="feac6-124">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using Windows Integrated Authentication.</span></span> <span data-ttu-id="feac6-125">これは、推奨される認証方法です。</span><span class="sxs-lookup"><span data-stu-id="feac6-125">This is the preferred authentication method.</span></span>  
  
 <span data-ttu-id="feac6-126">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="feac6-126">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="feac6-127">保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、SQL Server 認証を使用してサーバーに接続するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="feac6-127">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="feac6-128">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="feac6-128">**User name**</span></span>  
 <span data-ttu-id="feac6-129">保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択し、SQL Server 認証を使用してサーバーに接続することを指定した場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="feac6-129">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name.</span></span>  
  
 <span data-ttu-id="feac6-130">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="feac6-130">**Password**</span></span>  
 <span data-ttu-id="feac6-131">保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択し、SQL Server 認証を使用してサーバーに接続することを指定した場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="feac6-131">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] password.</span></span>  
  
### <a name="target--file-system"></a><span data-ttu-id="feac6-132">[変換先] = [ファイル システム]</span><span class="sxs-lookup"><span data-stu-id="feac6-132">Target = File System</span></span>  
 <span data-ttu-id="feac6-133">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="feac6-133">**File name**</span></span>  
 <span data-ttu-id="feac6-134">ファイルの保存先を選択した場合は、変換先ファイルのパスを入力するか、[**参照**] ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="feac6-134">When you have selected a file destination, type the path for the destination file, or use the **Browse** button.</span></span>  
  
 <span data-ttu-id="feac6-135">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="feac6-135">**Browse**</span></span>  
 <span data-ttu-id="feac6-136">ファイルの保存先を選択したら、[**パッケージの保存**] ダイアログボックスを使用して目的のファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="feac6-136">When you have selected a file destination, browse to the destination file by using the **Save Package** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feac6-137">参照</span><span class="sxs-lookup"><span data-stu-id="feac6-137">See Also</span></span>  
 [<span data-ttu-id="feac6-138">パッケージを保存する</span><span class="sxs-lookup"><span data-stu-id="feac6-138">Save Packages</span></span>](../save-packages.md)  
  
  
