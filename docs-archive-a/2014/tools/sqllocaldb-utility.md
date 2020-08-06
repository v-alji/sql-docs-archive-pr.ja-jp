---
title: SqlLocalDB Utility |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfb95cea4365d56c296d14fcc09046cd7eddc0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711237"
---
# <a name="sqllocaldb-utility"></a><span data-ttu-id="920bd-102">SqlLocalDB ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="920bd-102">SqlLocalDB Utility</span></span>
  <span data-ttu-id="920bd-103">`SqlLocalDB`LocalDB のインスタンスを作成するには、ユーティリティを使用し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] **LocalDB**ます。</span><span class="sxs-lookup"><span data-stu-id="920bd-103">Use the `SqlLocalDB` utility to create an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)]**LocalDB**.</span></span> <span data-ttu-id="920bd-104">`SqlLocalDB`ユーティリティ (SqlLocalDB.exe) は、ユーザーおよび開発者が LocalDB のインスタンスを作成および管理できるようにするための単純なコマンドラインツールです [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**。</span><span class="sxs-lookup"><span data-stu-id="920bd-104">The `SqlLocalDB` utility (SqlLocalDB.exe) is a simple command line tool to enable users and developers to create and manage an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="920bd-105">**Localdb**の使用方法の詳細については、「 [SQL Server 2014 Express localdb](../database-engine/configure-windows/sql-server-2016-express-localdb.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="920bd-105">For information about how to use **LocalDB**, see [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="920bd-106">構文</span><span class="sxs-lookup"><span data-stu-id="920bd-106">Syntax</span></span>  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="920bd-107">引数</span><span class="sxs-lookup"><span data-stu-id="920bd-107">Arguments</span></span>  
 <span data-ttu-id="920bd-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* **[-s]**</span><span class="sxs-lookup"><span data-stu-id="920bd-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [**-s** ]</span></span>  
 <span data-ttu-id="920bd-109">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** の新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="920bd-109">Creates a new of instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="920bd-110">`SqlLocalDB`[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]引数で指定されたバージョンのバイナリを使用し *\<instance-version>* ます。</span><span class="sxs-lookup"><span data-stu-id="920bd-110">`SqlLocalDB` uses the version of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] binaries specified by *\<instance-version>* argument.</span></span> <span data-ttu-id="920bd-111">バージョン番号は、1 桁以上の 10 進数の数値書式で指定します。</span><span class="sxs-lookup"><span data-stu-id="920bd-111">The version number is specified in numeric format with at least one decimal.</span></span> <span data-ttu-id="920bd-112">マイナー バージョン番号 (サービス パック) は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="920bd-112">The minor version numbers (service packs) are optional.</span></span> <span data-ttu-id="920bd-113">たとえば、次の 2 つのバージョン番号のどちらも使用できます。11.0 または 11.0.1186。</span><span class="sxs-lookup"><span data-stu-id="920bd-113">For example the following two version numbers are both acceptable: 11.0, or 11.0.1186.</span></span> <span data-ttu-id="920bd-114">指定したバージョンがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="920bd-114">The specified version must be installed on the computer.</span></span> <span data-ttu-id="920bd-115">指定しない場合、バージョン番号は既定でユーティリティのバージョンに `SqlLocalDB` なります。</span><span class="sxs-lookup"><span data-stu-id="920bd-115">If not specified, the version number defaults to the version of the `SqlLocalDB` utility.</span></span> <span data-ttu-id="920bd-116">**-s** を追加した場合、**LocalDB** の新しいインスタンスが起動します。</span><span class="sxs-lookup"><span data-stu-id="920bd-116">Adding **-s** starts the new instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="920bd-117">[ **share** | **h** ]</span><span class="sxs-lookup"><span data-stu-id="920bd-117">[ **share** | **h** ]</span></span>  
 <span data-ttu-id="920bd-118">指定された共有名を使用して、 **LocalDB** の指定されたプライベート インスタンスを共有します。</span><span class="sxs-lookup"><span data-stu-id="920bd-118">Shares the specified private instance of **LocalDB** using the specified shared name.</span></span> <span data-ttu-id="920bd-119">ユーザー SID またはアカウント名を省略した場合、既定で現在のユーザーになります。</span><span class="sxs-lookup"><span data-stu-id="920bd-119">If the user SID or account name is omitted, it defaults to the current user.</span></span>  
  
 <span data-ttu-id="920bd-120">[ **unshared** | **u** ]</span><span class="sxs-lookup"><span data-stu-id="920bd-120">[ **unshared** | **u** ]</span></span>  
 <span data-ttu-id="920bd-121">**LocalDB**の指定した共有インスタンスの共有を停止します。</span><span class="sxs-lookup"><span data-stu-id="920bd-121">Stops the sharing of the specified shared instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="920bd-122">[ **delete** | **d** ] *\<instance-name>*</span><span class="sxs-lookup"><span data-stu-id="920bd-122">[ **delete** | **d** ] *\<instance-name>*</span></span>  
 <span data-ttu-id="920bd-123">指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="920bd-123">Deletes the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span>  
  
 <span data-ttu-id="920bd-124">[ **start** | **s** ] " *\<instance-name>* "</span><span class="sxs-lookup"><span data-stu-id="920bd-124">[ **start** | **s** ] "*\<instance-name>*"</span></span>  
 <span data-ttu-id="920bd-125">指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="920bd-125">Starts the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="920bd-126">成功した場合、ステートメントから **LocalDB**の名前付きパイプ アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="920bd-126">When successful the statement returns the named pipe address of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="920bd-127">[ **stop** | **p** ] *\<instance-name>* **[-i]** **[-k]**</span><span class="sxs-lookup"><span data-stu-id="920bd-127">[ **stop** | **p** ] *\<instance-name>* [**-i** ] [**-k** ]</span></span>  
 <span data-ttu-id="920bd-128">指定した [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを停止します。</span><span class="sxs-lookup"><span data-stu-id="920bd-128">Stops the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="920bd-129">**-I**を追加すると、オプションを使用してインスタンスのシャットダウンが要求され `NOWAIT` ます。</span><span class="sxs-lookup"><span data-stu-id="920bd-129">Adding **-i** requests the instance shutdown with the `NOWAIT` option.</span></span> <span data-ttu-id="920bd-130">**-k** を追加した場合は、インスタンス プロセスに通知することなく、そのプロセスを停止します。</span><span class="sxs-lookup"><span data-stu-id="920bd-130">Adding **-k** kills the instance process without contacting it.</span></span>  
  
 <span data-ttu-id="920bd-131">[ **info** | **i** ] [ *\<instance-name>* ]</span><span class="sxs-lookup"><span data-stu-id="920bd-131">[ **info** | **i** ] [ *\<instance-name>* ]</span></span>  
 <span data-ttu-id="920bd-132">現在のユーザーが所有する [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のすべてのインスタンスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="920bd-132">Lists all instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** owned by the current user.</span></span>  
  
 <span data-ttu-id="920bd-133">*\<instance-name>* を指定すると、[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** の指定したインスタンスの名前、バージョン、状態 (Running または Stopped)、および最後の起動時刻に加え、**LocalDB** のローカル パイプ名が返されます。</span><span class="sxs-lookup"><span data-stu-id="920bd-133">*\<instance-name>* returns the name, version, state (Running or Stopped), last start time for the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**, and the local pipe name of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="920bd-134">[ **trace** | **t** ] **on** | **off**</span><span class="sxs-lookup"><span data-stu-id="920bd-134">[ **trace** | **t** ] **on** | **off**</span></span>  
 <span data-ttu-id="920bd-135">**trace on**は、現在の `SqlLocalDB` ユーザーに対する API 呼び出しのトレースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="920bd-135">**trace on** enables tracing for the `SqlLocalDB` API calls for the current user.</span></span> <span data-ttu-id="920bd-136">**trace off** はトレースを無効にします。</span><span class="sxs-lookup"><span data-stu-id="920bd-136">**trace off** disables tracing.</span></span>  
  
 <span data-ttu-id="920bd-137">**-?**</span><span class="sxs-lookup"><span data-stu-id="920bd-137">**-?**</span></span>  
 <span data-ttu-id="920bd-138">各オプションの簡単な説明を返し `SqlLocalDB` ます。</span><span class="sxs-lookup"><span data-stu-id="920bd-138">Returns brief descriptions of each `SqlLocalDB` option.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="920bd-139">解説</span><span class="sxs-lookup"><span data-stu-id="920bd-139">Remarks</span></span>  
 <span data-ttu-id="920bd-140">引数 *instance name* は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子のルールに従っているか、二重引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="920bd-140">The *instance name* argument must follow the rules for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers or it must be enclosed in double quotes.</span></span>  
  
 <span data-ttu-id="920bd-141">引数を指定せずに SqlLocalDB を実行すると、ヘルプ テキストが返されます。</span><span class="sxs-lookup"><span data-stu-id="920bd-141">Executing SqlLocalDB without arguments returns the help text.</span></span>  
  
 <span data-ttu-id="920bd-142">start 以外の操作は、現在ログインしているユーザーに属するインスタンスでのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="920bd-142">Operations other than start can only be performed on an instance belonging to currently logged in user.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="920bd-143">例</span><span class="sxs-lookup"><span data-stu-id="920bd-143">Examples</span></span>  
  
### <a name="a-creating-an-instance-of-localdb"></a><span data-ttu-id="920bd-144">A.</span><span class="sxs-lookup"><span data-stu-id="920bd-144">A.</span></span> <span data-ttu-id="920bd-145">LocalDB のインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="920bd-145">Creating an Instance of LocalDB</span></span>  
 <span data-ttu-id="920bd-146">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] バイナリを使用して `DEPARTMENT` という名前の [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** のインスタンスを作成し、そのインスタンスを起動する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="920bd-146">The following example creates an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** named `DEPARTMENT` using the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] binaries and starts the instance.</span></span>  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a><span data-ttu-id="920bd-147">B.</span><span class="sxs-lookup"><span data-stu-id="920bd-147">B.</span></span> <span data-ttu-id="920bd-148">LocalDB の共有インスタンスを操作する</span><span class="sxs-lookup"><span data-stu-id="920bd-148">Working with a Shared Instance of LocalDB</span></span>  
 <span data-ttu-id="920bd-149">管理者権限を使用してコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="920bd-149">Open a command prompt using Administrator privileges.</span></span>  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 <span data-ttu-id="920bd-150">次のコードを実行して、 **ログインを使用して、** LocalDB `NewLogin` の共有インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="920bd-150">Execute the following code to connect to the shared instance of **LocalDB** using the `NewLogin` login.</span></span>  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a><span data-ttu-id="920bd-151">参照</span><span class="sxs-lookup"><span data-stu-id="920bd-151">See Also</span></span>  
 [<span data-ttu-id="920bd-152">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="920bd-152">SQL Server 2014 Express LocalDB</span></span>](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
