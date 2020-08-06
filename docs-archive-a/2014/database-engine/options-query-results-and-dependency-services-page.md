---
title: '[オプション] ([クエリ結果と依存サービス] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 356714ee933fb40eda7038f4088309b6187f3ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644139"
---
# <a name="options-query-results-and-dependency-services-page"></a><span data-ttu-id="8fa15-102">[オプション] ([クエリ結果] および [依存サービス] ページ)</span><span class="sxs-lookup"><span data-stu-id="8fa15-102">Options (Query Results and Dependency Services Page)</span></span>
  <span data-ttu-id="8fa15-103">このページを使用すると、依存サービスのために接続するサーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8fa15-103">Use this page to specify the server to connect for Dependency Services.</span></span> <span data-ttu-id="8fa15-104">依存サービスを使用すると、異なるサーバーに格納されている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの間の依存関係に関する情報を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="8fa15-104">Dependency Services enables you to extract information about dependencies between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects stored on different servers.</span></span> <span data-ttu-id="8fa15-105">オブジェクトの依存関係を表示するには、の [**オブジェクトの依存関係**] ダイアログボックスを使用し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8fa15-105">You view object dependencies by using the **Object Dependencies** dialog box in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="8fa15-106">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="8fa15-106">**What do you want to do?**</span></span>  
  
1.  <span data-ttu-id="8fa15-107">[[オプション] ([クエリ結果]/[依存サービス] ページ) ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="8fa15-107">[Open the Options (Query Results/Dependency Services Page) Dialog Box](#open_dialog)</span></span>  
  
2.  [<span data-ttu-id="8fa15-108">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="8fa15-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a><span data-ttu-id="8fa15-109">[オプション] ([クエリ結果]/[依存サービス] ページ) ダイアログボックスを開く</span><span class="sxs-lookup"><span data-stu-id="8fa15-109">Open the Options (Query Results/Dependency Services Page) Dialog Box</span></span>  
  
1.  <span data-ttu-id="8fa15-110">で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] [**ツール**] メニューの [**オプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fa15-110">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], click **Options** on the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="8fa15-111">**[クエリ結果]** を展開し、**[依存サービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8fa15-111">Expand **Query Results**, and then click **Dependency Services**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="8fa15-112">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="8fa15-112">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="8fa15-113">Options</span><span class="sxs-lookup"><span data-stu-id="8fa15-113">Options</span></span>  
 <span data-ttu-id="8fa15-114">**[依存サービス サーバー]**</span><span class="sxs-lookup"><span data-stu-id="8fa15-114">**Dependency Services server**</span></span>  
 <span data-ttu-id="8fa15-115">依存サービスがインストールされているサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="8fa15-115">Specify the server that Dependency Services is installed on.</span></span>  
  
 <span data-ttu-id="8fa15-116">**認証**</span><span class="sxs-lookup"><span data-stu-id="8fa15-116">**Authentication**</span></span>  
 <span data-ttu-id="8fa15-117">Microsoft Windows ユーザー アカウントを使用してログオンする場合は、[Windows 認証] を選択します。そうでない場合は、[SQL Server 認証] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8fa15-117">Select Windows Authentication to log on using a Microsoft Windows user account, or select SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="8fa15-118">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、SQL Server は SQL Server ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="8fa15-118">When a user connects with a specified login name and password from a non-trusted connection, SQL Server performs the authentication by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="8fa15-119">ログイン アカウントが見つからない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="8fa15-119">If SQL Server cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="8fa15-120">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="8fa15-120">**User name**</span></span>  
 <span data-ttu-id="8fa15-121">SQL Server 認証を使用する場合は、ユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="8fa15-121">If using SQL Server Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="8fa15-122">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="8fa15-122">**Password**</span></span>  
 <span data-ttu-id="8fa15-123">SQL Server 認証を使用する場合は、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8fa15-123">If using SQL Server Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="8fa15-124">**テスト**</span><span class="sxs-lookup"><span data-stu-id="8fa15-124">**Test**</span></span>  
 <span data-ttu-id="8fa15-125">クリックすると、接続がテストされます。</span><span class="sxs-lookup"><span data-stu-id="8fa15-125">Click to test the connection.</span></span>