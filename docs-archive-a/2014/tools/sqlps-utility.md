---
title: sqlps ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: b445366b3fb99ad4beebdf7b203ada77afe90c8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711213"
---
# <a name="sqlps-utility"></a><span data-ttu-id="16037-102">sqlps ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="16037-102">sqlps Utility</span></span>
  <span data-ttu-id="16037-103">`sqlps` ユーティリティは、Windows PowerShell 2.0 セッションを起動し、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーおよびコマンドレットの読み込みと登録を行います。</span><span class="sxs-lookup"><span data-stu-id="16037-103">The `sqlps` utility starts a Windows PowerShell 2.0 session with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and cmdlets loaded and registered.</span></span> <span data-ttu-id="16037-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell コンポーネントを使用する PowerShell コマンドやスクリプトを入力して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとそのオブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="16037-104">You can enter PowerShell commands or scripts that use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components to work with instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and their objects.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="16037-105">代わりに `sqlps` PowerShell モジュールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="16037-105">Use the `sqlps` PowerShell module instead.</span></span> <span data-ttu-id="16037-106">モジュールの詳細については `sqlps` 、「 [Sqlps モジュールのインポート](../database-engine/import-the-sqlps-module.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16037-106">For more information about the `sqlps` module, see [Import the SQLPS Module](../database-engine/import-the-sqlps-module.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16037-107">構文</span><span class="sxs-lookup"><span data-stu-id="16037-107">Syntax</span></span>  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="16037-108">引数</span><span class="sxs-lookup"><span data-stu-id="16037-108">Arguments</span></span>  
 <span data-ttu-id="16037-109">**-NoLogo**</span><span class="sxs-lookup"><span data-stu-id="16037-109">**-NoLogo**</span></span>  
 <span data-ttu-id="16037-110">`sqlps` ユーティリティの起動時に著作権画面を表示しないように指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-110">Specifies that the `sqlps` utility hide the copyright banner when it starts.</span></span>  
  
 <span data-ttu-id="16037-111">**-NoExit**</span><span class="sxs-lookup"><span data-stu-id="16037-111">**-NoExit**</span></span>  
 <span data-ttu-id="16037-112">スタートアップ コマンドの完了後に `sqlps` ユーティリティの実行を継続するように指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-112">Specifies that the `sqlps` utility continue running after the startup commands have completed.</span></span>  
  
 <span data-ttu-id="16037-113">**-NoProfile**</span><span class="sxs-lookup"><span data-stu-id="16037-113">**-NoProfile**</span></span>  
 <span data-ttu-id="16037-114">`sqlps` ユーティリティがユーザー プロファイルを読み込まないように指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-114">Specifies that the `sqlps` utility not load a user profile.</span></span> <span data-ttu-id="16037-115">ユーザー プロファイルには、複数の PowerShell セッションで共通して使用する別名、関数、および変数が記録されます。</span><span class="sxs-lookup"><span data-stu-id="16037-115">User profiles record commonly used aliases, functions, and variables for use across PowerShell sessions.</span></span>  
  
 <span data-ttu-id="16037-116">**-OutPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="16037-116">**-OutPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="16037-117">ユーティリティの出力を、 `sqlps` テキスト文字列 (**テキスト**) またはシリアル化された Export-clixml 形式 (**XML**) のいずれかとして書式設定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-117">Specifies that the `sqlps` utility output be formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="16037-118">**-InPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="16037-118">**-InPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="16037-119">ユーティリティへの入力を、 `sqlps` テキスト文字列 (**テキスト**) またはシリアル化された Export-clixml 形式 (**XML**) のいずれかとして書式設定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-119">Specifies that input to the `sqlps` utility is formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="16037-120">**-Command**</span><span class="sxs-lookup"><span data-stu-id="16037-120">**-Command**</span></span>  
 <span data-ttu-id="16037-121">`sqlps` ユーティリティで実行するコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-121">Specifies the command for the `sqlps` utility to run.</span></span> <span data-ttu-id="16037-122">`sqlps` **-NoExit**も指定されていない限り、ユーティリティはコマンドを実行してから終了します。</span><span class="sxs-lookup"><span data-stu-id="16037-122">The `sqlps` utility runs the command and then exits, unless **-NoExit** is also specified.</span></span> <span data-ttu-id="16037-123">**-Command**の後にはその他のスイッチを指定しないでください。指定すると、コマンド パラメーターとして読み取られます。</span><span class="sxs-lookup"><span data-stu-id="16037-123">Do not specify any other switches after **-Command**, they will be read as command parameters.</span></span>  
  
 **-**  
 <span data-ttu-id="16037-124">**-Command-** ユーティリティが標準入力からの入力を読み取ることを指定し `sqlps` ます。</span><span class="sxs-lookup"><span data-stu-id="16037-124">**-Command-** specifies that the `sqlps` utility read the input from the standard input.</span></span>  
  
 <span data-ttu-id="16037-125">*script_block* [ **-args**_argument_array_ ]</span><span class="sxs-lookup"><span data-stu-id="16037-125">*script_block* [ **-args**_argument_array_ ]</span></span>  
 <span data-ttu-id="16037-126">実行する PowerShell コマンドのブロックを指定します。ブロックは中かっこ {} で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="16037-126">Specifies a block of PowerShell commands to run, the block must be enclosed in braces: {}.</span></span> <span data-ttu-id="16037-127">*Script_block*は、 `sqlps` ユーティリティが**PowerShell**または別のユーティリティセッションから呼び出された場合にのみ指定でき `sqlps` ます。</span><span class="sxs-lookup"><span data-stu-id="16037-127">*Script_block* can only be specified when the `sqlps` utility is called from either **PowerShell** or another `sqlps` utility session.</span></span> <span data-ttu-id="16037-128">*argument_array* は、 *script_block*内の PowerShell コマンドの引数を含む PowerShell 変数の配列です。</span><span class="sxs-lookup"><span data-stu-id="16037-128">The *argument_array* is an array of PowerShell variables containing the arguments for the PowerShell commands in the *script_block*.</span></span>  
  
 <span data-ttu-id="16037-129">*string* [ *command_parameters* ]</span><span class="sxs-lookup"><span data-stu-id="16037-129">*string* [ *command_parameters* ]</span></span>  
 <span data-ttu-id="16037-130">実行する PowerShell コマンドを含む文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="16037-130">Specifies a string that contains the PowerShell commands to be run.</span></span> <span data-ttu-id="16037-131">**"& { *`command`* }"** の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="16037-131">Use the format **"&{*`command`*}"**.</span></span> <span data-ttu-id="16037-132">引用符は文字列を示し、invoke 演算子 (&) によって `sqlps` ユーティリティによってコマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="16037-132">The quotation marks indicate a string, and the invoke operator (&) causes the `sqlps` utility to run the command.</span></span>  
  
 <span data-ttu-id="16037-133">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="16037-133">[ **-?**</span></span><span data-ttu-id="16037-134"> |  **-Help** ]</span><span class="sxs-lookup"><span data-stu-id="16037-134"> | **-Help** ]</span></span>  
 <span data-ttu-id="16037-135">`sqlps` ユーティリティ オプションの構文の概要を表示します。</span><span class="sxs-lookup"><span data-stu-id="16037-135">Shows the syntax summary of the `sqlps` utility options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16037-136">解説</span><span class="sxs-lookup"><span data-stu-id="16037-136">Remarks</span></span>  
 <span data-ttu-id="16037-137">ユーティリティは、 `sqlps` powershell 環境 (PowerShell.exe) を起動し、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] powershell モジュールを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="16037-137">The `sqlps` utility starts the PowerShell environment (PowerShell.exe) and loads the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell module.</span></span> <span data-ttu-id="16037-138">モジュールは、という名前の `sqlps` PowerShell スナップインを読み込んで登録し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="16037-138">The module, also named `sqlps`, loads and registers these [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins:</span></span>  
  
-   <span data-ttu-id="16037-139">Microsoft.SqlServer.Management.PSProvider.dll</span><span class="sxs-lookup"><span data-stu-id="16037-139">Microsoft.SqlServer.Management.PSProvider.dll</span></span>  
  
     <span data-ttu-id="16037-140">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーおよび関連するコマンドレット ( **Encode-SqlName** や **Decode-SqlName**など) を実装します。</span><span class="sxs-lookup"><span data-stu-id="16037-140">Implements the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and associated cmdlets such as **Encode-SqlName** and **Decode-SqlName**.</span></span>  
  
-   <span data-ttu-id="16037-141">Microsoft.SqlServer.Management.PSSnapin.dll</span><span class="sxs-lookup"><span data-stu-id="16037-141">Microsoft.SqlServer.Management.PSSnapin.dll</span></span>  
  
     <span data-ttu-id="16037-142">**Invoke-Sqlcmd** および **Invoke-PolicyEvaluation** コマンドレットを実装します。</span><span class="sxs-lookup"><span data-stu-id="16037-142">Implements the **Invoke-Sqlcmd** and **Invoke-PolicyEvaluation** cmdlets.</span></span>  
  
 <span data-ttu-id="16037-143">`sqlps` ユーティリティを使用して、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="16037-143">You can use the `sqlps` utility to do the following:</span></span>  
  
-   <span data-ttu-id="16037-144">PowerShell コマンドを対話的に実行する。</span><span class="sxs-lookup"><span data-stu-id="16037-144">Interactively run PowerShell commands.</span></span>  
  
-   <span data-ttu-id="16037-145">PowerShell スクリプト ファイルを実行する。</span><span class="sxs-lookup"><span data-stu-id="16037-145">Run PowerShell script files.</span></span>  
  
-   <span data-ttu-id="16037-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コマンドレットを実行する。</span><span class="sxs-lookup"><span data-stu-id="16037-146">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="16037-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダー パスを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの階層内を移動する。</span><span class="sxs-lookup"><span data-stu-id="16037-147">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="16037-148">既定では、 `sqlps` スクリプト実行ポリシーが "**制限付き**" に設定された状態でユーティリティが実行されます。</span><span class="sxs-lookup"><span data-stu-id="16037-148">By default, the `sqlps` utility runs with the scripting execution policy set to **Restricted**.</span></span> <span data-ttu-id="16037-149">これにより、PowerShell スクリプトの実行が防止されます。</span><span class="sxs-lookup"><span data-stu-id="16037-149">This prevents running any PowerShell scripts.</span></span> <span data-ttu-id="16037-150">**Set-ExecutionPolicy** コマンドレットを使用すると、署名されたスクリプトまたは任意のスクリプトの実行を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="16037-150">You can use the **Set-ExecutionPolicy** cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="16037-151">信頼できるソースからのスクリプト以外は実行しないでください。また、適切な NTFS 権限を使用して、すべての入力ファイルと出力ファイルのセキュリティを保護してください。</span><span class="sxs-lookup"><span data-stu-id="16037-151">Only run scripts from trusted sources, and secure all input and output files by using the appropriate NTFS permissions.</span></span> <span data-ttu-id="16037-152">PowerShell スクリプトの有効化の詳細については、「 [Windows PowerShell スクリプトの実行](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16037-152">For more information about enabling PowerShell scripts, see [Running Windows PowerShell Scripts](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).</span></span>  
  
 <span data-ttu-id="16037-153">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] および [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] に採用されていたバージョンの `sqlps` ユーティリティは、Windows PowerShell 1.0 のミニシェルとして実装されていました。</span><span class="sxs-lookup"><span data-stu-id="16037-153">The version of the `sqlps` utility in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] was implemented as a Windows PowerShell 1.0 mini-shell.</span></span> <span data-ttu-id="16037-154">ミニシェルには特定の制限があります。たとえば、ミニシェルによって読み込まれているスナップイン以外、ユーザーは読み込むことができません。</span><span class="sxs-lookup"><span data-stu-id="16037-154">Mini-shells have certain restrictions, such as not allowing users to load snap-ins other than those loaded by the mini-shell.</span></span> <span data-ttu-id="16037-155">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 以降のバージョンのユーティリティは、`sqlps` モジュールを使用するように変更されており、このような制限は適用されません。</span><span class="sxs-lookup"><span data-stu-id="16037-155">These restrictions do not apply to the [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] and higher versions of the utility, which have been changed to use the `sqlps` module.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="16037-156">例</span><span class="sxs-lookup"><span data-stu-id="16037-156">Examples</span></span>  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a><span data-ttu-id="16037-157">A.</span><span class="sxs-lookup"><span data-stu-id="16037-157">A.</span></span> <span data-ttu-id="16037-158">既定の対話モードで著作権画面を表示せずに sqlps ユーティリティを実行する</span><span class="sxs-lookup"><span data-stu-id="16037-158">Run the sqlps utility in default, interactive mode without the copyright banner</span></span>
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a><span data-ttu-id="16037-159">B.</span><span class="sxs-lookup"><span data-stu-id="16037-159">B.</span></span> <span data-ttu-id="16037-160">コマンド プロンプトから SQL Server PowerShell スクリプトを実行する</span><span class="sxs-lookup"><span data-stu-id="16037-160">Run a SQL Server PowerShell script from the command prompt</span></span>
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a><span data-ttu-id="16037-161">C.</span><span class="sxs-lookup"><span data-stu-id="16037-161">C.</span></span> <span data-ttu-id="16037-162">コマンド プロンプトから SQL Server PowerShell スクリプトを実行し、スクリプト完了後も実行を続ける</span><span class="sxs-lookup"><span data-stu-id="16037-162">Run a SQL Server PowerShell script from the command prompt, and keep running after the script completes</span></span>
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a><span data-ttu-id="16037-163">参照</span><span class="sxs-lookup"><span data-stu-id="16037-163">See Also</span></span>  
 <span data-ttu-id="16037-164">[サーバー ネットワーク プロトコルの有効化または無効化](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="16037-164">[Enable or Disable a Server Network Protocol](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 [<span data-ttu-id="16037-165">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="16037-165">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
