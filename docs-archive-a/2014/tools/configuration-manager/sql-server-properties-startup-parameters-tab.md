---
title: SQL Server のプロパティ] ([起動時のパラメーター] タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 16942624-5374-446c-8de4-ee6ed34d6e94
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66c4b71433face008ba78af93579cf175fb4bed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640296"
---
# <a name="sql-server-properties-startup-parameters-tab"></a><span data-ttu-id="42ff3-102">[SQL Server のプロパティ] ダイアログ ボックス ([起動時のパラメーター] タブ)</span><span class="sxs-lookup"><span data-stu-id="42ff3-102">SQL Server Properties (Startup Parameters Tab)</span></span>
  <span data-ttu-id="42ff3-103">このダイアログ ボックスを使用すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の起動時のパラメーターを追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-103">Use this dialog box to add or remove startup parameters for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="42ff3-104">起動時のパラメーターは [!INCLUDE[ssDE](../../includes/ssde-md.md)] のパフォーマンスに大きな影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-104">Startup parameters can have a large effect on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] performance.</span></span> <span data-ttu-id="42ff3-105">起動時のパラメーターを追加または変更する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスのスタートアップ オプションの使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42ff3-105">Before adding or changing startup parameters, see the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42ff3-106">オプション</span><span class="sxs-lookup"><span data-stu-id="42ff3-106">Options</span></span>  
 <span data-ttu-id="42ff3-107">**[起動時のパラメーターの指定]**</span><span class="sxs-lookup"><span data-stu-id="42ff3-107">**Specify a startup parameter**</span></span>  
 <span data-ttu-id="42ff3-108">パラメーターを追加するには、パラメーターを入力し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-108">To add a parameter, type the parameter, and then click **Add**.</span></span>  
  
 <span data-ttu-id="42ff3-109">必要なパラメーターのいずれかを変更するには、 **[既存のパラメーター]** ボックスのパラメーターを選択し、 **[起動時のパラメーターの指定]** ボックスの値を変更して、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-109">To modify one of the required parameters, select the parameter in the **Existing parameters** box, change the values in the **Specify a startup parameter** box, and then click **Update**.</span></span>  
  
 <span data-ttu-id="42ff3-110">**[既存のパラメーター]**</span><span class="sxs-lookup"><span data-stu-id="42ff3-110">**Existing parameters**</span></span>  
 <span data-ttu-id="42ff3-111">パラメーターを削除するには、パラメーターを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-111">To remove a parameter, select a parameter, and then click **Remove**.</span></span>  
  
## <a name="parameter-format"></a><span data-ttu-id="42ff3-112">パラメーターの形式</span><span class="sxs-lookup"><span data-stu-id="42ff3-112">Parameter Format</span></span>  
 <span data-ttu-id="42ff3-113">パラメーターの間に区切り記号を入力しないでください。</span><span class="sxs-lookup"><span data-stu-id="42ff3-113">Do not enter a separator between parameters.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="42ff3-114">構成マネージャーによって自動的に区切り記号が追加されます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-114">Configuration Manager automatically adds the separator.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="42ff3-115">構成マネージャーによって、次のパラメーターの要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-115">Configuration Manager enforces the following parameter requirements.</span></span>  
  
-   <span data-ttu-id="42ff3-116">先頭および末尾のスペースは、すべての起動時のパラメーターから削除します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-116">Leading and trailing spaces are trimmed from any startup parameter.</span></span>  
  
-   <span data-ttu-id="42ff3-117">すべての起動時のパラメーターの先頭文字は - (ダッシュ) で、2 番目の値は文字です。</span><span class="sxs-lookup"><span data-stu-id="42ff3-117">All startup parameters start with a - (dash) and the second value is a letter.</span></span>  
  
## <a name="required-parameters"></a><span data-ttu-id="42ff3-118">必須のパラメーター</span><span class="sxs-lookup"><span data-stu-id="42ff3-118">Required Parameters</span></span>  
 <span data-ttu-id="42ff3-119">以下のパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="42ff3-119">The following parameters are required.</span></span> <span data-ttu-id="42ff3-120">これらは変更できますが、削除できません。</span><span class="sxs-lookup"><span data-stu-id="42ff3-120">They can be changed but not removed.</span></span>  
  
-   <span data-ttu-id="42ff3-121">-d は、 **master.mdf** ファイル (master データベースのデータ ファイル) のパスです。</span><span class="sxs-lookup"><span data-stu-id="42ff3-121">-d is the path of the **master.mdf** file (the master database data file).</span></span>  
  
-   <span data-ttu-id="42ff3-122">-l は、 **master.ldf** ファイル (master データベースのログ ファイル) のパスです。</span><span class="sxs-lookup"><span data-stu-id="42ff3-122">-l is the path of the **master.ldf** file (the master database log file).</span></span>  
  
-   <span data-ttu-id="42ff3-123">-e は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログ ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="42ff3-123">-e is the path of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log files.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="42ff3-124">ファイル パス パラメーターが正しくない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は起動しません。</span><span class="sxs-lookup"><span data-stu-id="42ff3-124">If the file path parameters are incorrect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not start.</span></span>  
  
 <span data-ttu-id="42ff3-125">master データベースを移動する方法の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「システム データベースの移動」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42ff3-125">For more information about how to move the master database, see the topic "Moving System Databases" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="42ff3-126">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="42ff3-126">Optional Parameters</span></span>  
 <span data-ttu-id="42ff3-127">サポートされている、すべての起動時のパラメーターについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスのスタートアップ オプションの使用」で説明されています。</span><span class="sxs-lookup"><span data-stu-id="42ff3-127">All of the supported startup parameters are described in the topic "Using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Startup Options," in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="42ff3-128">起動時のパラメーターの -T*trace#* は、指定された有効なトレース フラグ ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace# *) を使用して*のインスタンスを起動することを指定します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-128">A startup parameter of -T*trace#* indicates that an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be started with a specified trace flag (*trace#*) in effect.</span></span> <span data-ttu-id="42ff3-129">トレース フラグを使用してサーバーが起動すると、標準的な動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="42ff3-129">Trace flags are used to start the server with nonstandard behavior.</span></span> <span data-ttu-id="42ff3-130">トレース フラグの詳細については、[!INCLUDE[tsql](../../includes/tsql-md.md)]オンライン ブックの「トレース フラグ ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42ff3-130">For more information about trace flags, see the topic "Trace Flags ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="42ff3-131">ドキュメントに未記載の起動時のパラメーターとトレース フラグについては、インターネット上で追加の説明を読むことができます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-131">You might see additional undocumented startup parameters and trace flags described on the Internet.</span></span> <span data-ttu-id="42ff3-132">ドキュメントに未記載の起動時のパラメーターとトレース フラグは、一般的ではない問題の解決またはテストに必要な特定の条件の適用のために作成されます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-132">Undocumented startup parameters and trace flags are created to address uncommon problems or to force certain conditions required for testing.</span></span> <span data-ttu-id="42ff3-133">ドキュメントに未記載の起動時のパラメーターを使用すると、予期しない結果になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="42ff3-133">Using undocumented startup parameters can have unexpected results.</span></span> <span data-ttu-id="42ff3-134">マイクロソフト カスタマー サポート サービスから指示されない限り、ドキュメントに未記載のパラメーターを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="42ff3-134">Do not use undocumented parameters unless directed by Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="42ff3-135">以下に、一般的な省略可能なパラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-135">The following list describes some common optional parameters.</span></span>  
  
|<span data-ttu-id="42ff3-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42ff3-136">Parameter</span></span>|<span data-ttu-id="42ff3-137">簡単な説明</span><span class="sxs-lookup"><span data-stu-id="42ff3-137">Short description</span></span>|  
|---------------|-----------------------|  
|<span data-ttu-id="42ff3-138">-M</span><span class="sxs-lookup"><span data-stu-id="42ff3-138">-m</span></span>|<span data-ttu-id="42ff3-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスをシングル ユーザー モードで起動します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-139">Starts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in single-user mode.</span></span>|  
|<span data-ttu-id="42ff3-140">-T1204</span><span class="sxs-lookup"><span data-stu-id="42ff3-140">-T1204</span></span>|<span data-ttu-id="42ff3-141">デッドロックに関係しているロックのリソースと種類、および影響を受けている現在のコマンドを返します。</span><span class="sxs-lookup"><span data-stu-id="42ff3-141">Returns the resources and types of locks participating in a deadlock and also the current command affected.</span></span>|  
|<span data-ttu-id="42ff3-142">-T1224</span><span class="sxs-lookup"><span data-stu-id="42ff3-142">-T1224</span></span>|<span data-ttu-id="42ff3-143">ロック数に基づいてロックのエスカレーションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-143">Disables lock escalation based on the number of locks.</span></span>|  
|<span data-ttu-id="42ff3-144">-T3608</span><span class="sxs-lookup"><span data-stu-id="42ff3-144">-T3608</span></span>|<span data-ttu-id="42ff3-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、master データベース以外のすべてのデータベースを自動的に開始および復旧しないようにします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-145">Prevents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from automatically starting and recovering any database except the master database.</span></span>|  
|<span data-ttu-id="42ff3-146">-T7806</span><span class="sxs-lookup"><span data-stu-id="42ff3-146">-T7806</span></span>|<span data-ttu-id="42ff3-147">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]で専用管理者接続 (DAC) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="42ff3-147">Enables a dedicated administrator connection (DAC) on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="42ff3-148">省略可能なパラメーターの中には、サーバーの動作を変更し、パフォーマンスに影響を与えるものもあります。</span><span class="sxs-lookup"><span data-stu-id="42ff3-148">Some optional parameters can change server behavior and may affect performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="42ff3-149">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="42ff3-149">Permissions</span></span>  
 <span data-ttu-id="42ff3-150">このページは、レジストリの関連エントリを変更できるユーザーのみが使用できます。</span><span class="sxs-lookup"><span data-stu-id="42ff3-150">Use of this page is restricted to users who can change the related entries in the registry.</span></span> <span data-ttu-id="42ff3-151">該当するユーザーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="42ff3-151">This includes the following users.</span></span>  
  
-   <span data-ttu-id="42ff3-152">ローカル管理者グループのメンバー。</span><span class="sxs-lookup"><span data-stu-id="42ff3-152">Members of the local administrators group.</span></span>  
  
-   <span data-ttu-id="42ff3-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって使用されるドメイン アカウント ( [!INCLUDE[ssDE](../../includes/ssde-md.md)] がドメイン アカウントで実行されるように構成されている場合)。</span><span class="sxs-lookup"><span data-stu-id="42ff3-153">The domain account that is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to run under a domain account.</span></span>  
  
## <a name="books-online-references"></a><span data-ttu-id="42ff3-154">オンライン ブックの参照</span><span class="sxs-lookup"><span data-stu-id="42ff3-154">Books Online References</span></span>  
 <span data-ttu-id="42ff3-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時のパラメーターの追加情報については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「サーバーのスタートアップ オプションを構成する方法 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャー)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42ff3-155">For additional information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup parameters, see "How to: Configure Server Startup Options ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
