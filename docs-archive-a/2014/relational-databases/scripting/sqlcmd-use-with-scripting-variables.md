---
title: sqlcmd でのスクリプト変数の使用
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server], sqlcmd utility
- variables [SQL Server], scripts
- scripting variables [SQL Server]
- sqlcmd utility, scripts
- setvar command
ms.assetid: 793495ca-cfc9-498d-8276-c44a5d09a92c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443cb400dc099726ba75bfcec2d38cee4ee2dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643771"
---
# <a name="use-sqlcmd-with-scripting-variables"></a><span data-ttu-id="ec697-102">sqlcmd でのスクリプト変数の使用</span><span class="sxs-lookup"><span data-stu-id="ec697-102">Use sqlcmd with Scripting Variables</span></span>
  <span data-ttu-id="ec697-103">スクリプトで使用される変数は、スクリプト変数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ec697-103">Variables that are used in scripts are called scripting variables.</span></span> <span data-ttu-id="ec697-104">スクリプト変数を使用すると、1 つのスクリプトを複数のシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec697-104">Scripting variables enable one script to be used in multiple scenarios.</span></span> <span data-ttu-id="ec697-105">たとえば、1 つのスクリプトを複数のサーバーに対して実行する場合、各サーバー用にスクリプトを変更するのではなく、サーバー名にスクリプト変数を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ec697-105">For example, if you want to run one script against multiple servers, instead of modifying the script for each server, you can use a scripting variable for the server name.</span></span> <span data-ttu-id="ec697-106">サーバー名をスクリプト変数で指定することで、同じスクリプトを複数のサーバーで実行することができるようになります。</span><span class="sxs-lookup"><span data-stu-id="ec697-106">By changing the server name supplied to the scripting variable, the same script can be executed on different servers.</span></span>  
  
 <span data-ttu-id="ec697-107">スクリプト変数は、 **setvar** コマンドを使用して明示的に定義するか、または **sqlcmd -v** オプションを使用して暗黙的に定義できます。</span><span class="sxs-lookup"><span data-stu-id="ec697-107">Scripting variables can be defined explicitly by using the **setvar** command, or implicitly by using the **sqlcmd-v** option.</span></span>  
  
 <span data-ttu-id="ec697-108">このトピックでは、 **SET**を使用して Cmd.exe コマンド プロンプトで環境変数を定義する例も紹介しています。</span><span class="sxs-lookup"><span data-stu-id="ec697-108">This topic also includes examples defining environmental variables at the Cmd.exe command prompt by using **SET**.</span></span>  
  
## <a name="setting-scripting-variables-by-using-the-setvar-command"></a><span data-ttu-id="ec697-109">setvar コマンドを使用したスクリプト変数の設定</span><span class="sxs-lookup"><span data-stu-id="ec697-109">Setting Scripting Variables by Using the setvar Command</span></span>  
 <span data-ttu-id="ec697-110">**setvar** コマンドは、スクリプト変数を定義するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="ec697-110">The **setvar** command is used to define scripting variables.</span></span> <span data-ttu-id="ec697-111">**setvar** コマンドを使用して定義されている変数は、内部的に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-111">Variables that are defined by using the **setvar** command are stored internally.</span></span> <span data-ttu-id="ec697-112">スクリプト変数は、 **SET**を使用してコマンド プロンプトで定義されている環境変数と混同しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec697-112">Scripting variables should not be confused with environment variables that are defined at the command prompt by using **SET**.</span></span> <span data-ttu-id="ec697-113">環境変数でもなく **setvar**コマンドを使用して定義したものでもない変数をスクリプト内で参照していると、エラー メッセージが表示され、スクリプトの実行は停止されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-113">If a script references a variable that is not an environment variable or is not defined by using **setvar**, an error message is returned and the execution of the script will stop.</span></span> <span data-ttu-id="ec697-114">詳細については、「 **sqlcmd ユーティリティ** 」の [-b](../../tools/sqlcmd-utility.md)オプションの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec697-114">For more information, see the **-b** option in [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="ec697-115">変数の優先順位 (低から高)</span><span class="sxs-lookup"><span data-stu-id="ec697-115">Variable Precedence (Low to High)</span></span>  
 <span data-ttu-id="ec697-116">複数の種類の変数に同じ名前が付いている場合、優先順位の最も高い変数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-116">If more than one type of variable has the same name, the variable with the highest precedence is used.</span></span>  
  
1.  <span data-ttu-id="ec697-117">システム レベル環境変数</span><span class="sxs-lookup"><span data-stu-id="ec697-117">System level environmental variables</span></span>  
  
2.  <span data-ttu-id="ec697-118">ユーザー レベル環境変数</span><span class="sxs-lookup"><span data-stu-id="ec697-118">User level environmental variables</span></span>  
  
3.  <span data-ttu-id="ec697-119">**sqlcmd**の起動前にコマンド プロンプトで設定されたコマンド シェル (**SET X=Y**)</span><span class="sxs-lookup"><span data-stu-id="ec697-119">Command shell (**SET X=Y**) set at command prompt before starting **sqlcmd**</span></span>  
  
4.  <span data-ttu-id="ec697-120">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="ec697-120">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="ec697-121">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="ec697-121">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec697-122">環境変数を表示するには、 **[コントロール パネル]** の **[システム]** アイコンを開き、 **[詳細設定]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec697-122">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="implicitly-setting-scripting-variables"></a><span data-ttu-id="ec697-123">スクリプト変数の暗黙的な設定</span><span class="sxs-lookup"><span data-stu-id="ec697-123">Implicitly Setting Scripting Variables</span></span>  
 <span data-ttu-id="ec697-124">関連する **sqlcmd** 変数を含むオプションを指定して **sqlcmd** を起動すると、 **sqlcmd** 変数には、そのオプションを使用して指定されている値が暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-124">When you start **sqlcmd** with an option that has a related **sqlcmd** variable, the **sqlcmd** variable is set implicitly to the value that is specified by using the option.</span></span> <span data-ttu-id="ec697-125">次の例では、 `sqlcmd` が `-l` オプションを指定して起動されています。</span><span class="sxs-lookup"><span data-stu-id="ec697-125">In the following example, `sqlcmd` is started with the `-l` option.</span></span> <span data-ttu-id="ec697-126">このコマンドを実行すると、SQLLOGINTIMEOUT 変数が暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-126">This implicitly sets the SQLLOGINTIMEOUT variable.</span></span>  
  
 `c:\> sqlcmd -l 60`  
  
 <span data-ttu-id="ec697-127">**-v** オプションを使用して、スクリプト内に存在するスクリプト変数を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec697-127">You can also use the **-v** option to set a scripting variable that exists in a script.</span></span> <span data-ttu-id="ec697-128">次のスクリプト (ファイル名は `testscript.sql`) では、 `ColumnName` がスクリプト変数です。</span><span class="sxs-lookup"><span data-stu-id="ec697-128">In the following script (the file name is `testscript.sql`), `ColumnName` is a scripting variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT x.$(ColumnName)`  
  
 `FROM Person.Person x`  
  
 <span data-ttu-id="ec697-129">`WHERE c.`BusinessEntityID `< 5;`</span><span class="sxs-lookup"><span data-stu-id="ec697-129">`WHERE c.`BusinessEntityID `< 5;`</span></span>  
  
 <span data-ttu-id="ec697-130">その後、 `-v` オプションを使用して、取得する列の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ec697-130">You can then specify the name of the column that you want returned by using the `-v` option:</span></span>  
  
 `sqlcmd -v ColumnName ="FirstName" -i c:\testscript.sql`  
  
 <span data-ttu-id="ec697-131">同じスクリプトを使用して別の列を取得するには、 `ColumnName` スクリプト変数の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="ec697-131">To return a different column by using the same script, change the value of the `ColumnName` scripting variable.</span></span>  
  
 `sqlcmd -v ColumnName ="LastName" -i c:\testscript.sql`  
  
## <a name="guidelines-for-scripting-variable-names-and-values"></a><span data-ttu-id="ec697-132">スクリプト変数の名前と値に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="ec697-132">Guidelines for Scripting Variable Names and Values</span></span>  
 <span data-ttu-id="ec697-133">スクリプト変数に名前を指定する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ec697-133">Consider the following guidelines when you name scripting variables:</span></span>  
  
-   <span data-ttu-id="ec697-134">変数名には空白文字または引用符を使用できません。</span><span class="sxs-lookup"><span data-stu-id="ec697-134">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="ec697-135">変数名には、 *$(var)* のような変数式と同じ形式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ec697-135">Variable names must not have the same form as a variable expression, such as *$(var)*.</span></span>  
  
-   <span data-ttu-id="ec697-136">スクリプト変数では、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="ec697-136">Scripting variables are case-insensitive</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec697-137">**sqlcmd** 環境変数に値が割り当てられていない場合、この変数は削除されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-137">If no value is assigned to a **sqlcmd** environment variable, the variable is removed.</span></span> <span data-ttu-id="ec697-138">値を指定せずに **:setvar VarName** を使用すると、変数は削除されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-138">Using **:setvar VarName** without a value clears the variable.</span></span>  
  
 <span data-ttu-id="ec697-139">スクリプト変数に値を指定する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ec697-139">Consider the following guidelines when you specify values for scripting variables:</span></span>  
  
-   <span data-ttu-id="ec697-140">**setvar** または **-v** オプションを使用して定義する変数値は、空白を含む文字列値の場合に引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec697-140">Variable values that are defined by using **setvar** or the **-v** option must be enclosed by quotation marks if the string value contains spaces.</span></span>  
  
-   <span data-ttu-id="ec697-141">変数値に引用符が使用されている場合は、その引用符をエスケープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec697-141">If quotation marks are part of the variable value, they must be escaped.</span></span> <span data-ttu-id="ec697-142">たとえば、`setvar MyVar "spac""e"`のように指定します。</span><span class="sxs-lookup"><span data-stu-id="ec697-142">For example: :`setvar MyVar "spac""e"`.</span></span>  
  
## <a name="guidelines-for-cmdexe-set-variable-values-and-names"></a><span data-ttu-id="ec697-143">Cmd.exe の SET による変数の値と名前に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="ec697-143">Guidelines for Cmd.exe SET Variable Values and Names</span></span>  
 <span data-ttu-id="ec697-144">SET を使用して定義される変数は、Cmd.exe 環境で使用されるため、 **sqlcmd**で参照できます。</span><span class="sxs-lookup"><span data-stu-id="ec697-144">Variables that are defined by using SET are part of the Cmd.exe environment and can be referenced by **sqlcmd**.</span></span> <span data-ttu-id="ec697-145">次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="ec697-145">Consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="ec697-146">変数名には空白文字または引用符を使用できません。</span><span class="sxs-lookup"><span data-stu-id="ec697-146">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="ec697-147">変数値には空白文字または引用符を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec697-147">Variable values may contain spaces or quotation marks.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="ec697-148">sqlcmd スクリプト変数</span><span class="sxs-lookup"><span data-stu-id="ec697-148">sqlcmd Scripting Variables</span></span>  
 <span data-ttu-id="ec697-149">**sqlcmd** で定義される変数はスクリプト変数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ec697-149">Variables that are defined by **sqlcmd** are known as scripting variables.</span></span> <span data-ttu-id="ec697-150">次の表は、 **sqlcmd** スクリプト変数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="ec697-150">The following table lists **sqlcmd** scripting variables.</span></span>  
  
|<span data-ttu-id="ec697-151">変数</span><span class="sxs-lookup"><span data-stu-id="ec697-151">Variable</span></span>|<span data-ttu-id="ec697-152">関連するオプション</span><span class="sxs-lookup"><span data-stu-id="ec697-152">Related option</span></span>|<span data-ttu-id="ec697-153">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-153">R/W</span></span>|<span data-ttu-id="ec697-154">Default</span><span class="sxs-lookup"><span data-stu-id="ec697-154">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="ec697-155">SQLCMDUSER\*</span><span class="sxs-lookup"><span data-stu-id="ec697-155">SQLCMDUSER\*</span></span>|<span data-ttu-id="ec697-156">-U</span><span class="sxs-lookup"><span data-stu-id="ec697-156">-U</span></span>|<span data-ttu-id="ec697-157">R</span><span class="sxs-lookup"><span data-stu-id="ec697-157">R</span></span>|<span data-ttu-id="ec697-158">""</span><span class="sxs-lookup"><span data-stu-id="ec697-158">""</span></span>|  
|<span data-ttu-id="ec697-159">SQLCMDPASSWORD\*</span><span class="sxs-lookup"><span data-stu-id="ec697-159">SQLCMDPASSWORD\*</span></span>|<span data-ttu-id="ec697-160">-P</span><span class="sxs-lookup"><span data-stu-id="ec697-160">-P</span></span>|--|<span data-ttu-id="ec697-161">""</span><span class="sxs-lookup"><span data-stu-id="ec697-161">""</span></span>|  
|<span data-ttu-id="ec697-162">SQLCMDSERVER\*</span><span class="sxs-lookup"><span data-stu-id="ec697-162">SQLCMDSERVER\*</span></span>|<span data-ttu-id="ec697-163">-S</span><span class="sxs-lookup"><span data-stu-id="ec697-163">-S</span></span>|<span data-ttu-id="ec697-164">R</span><span class="sxs-lookup"><span data-stu-id="ec697-164">R</span></span>|<span data-ttu-id="ec697-165">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="ec697-165">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="ec697-166">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="ec697-166">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="ec697-167">-H</span><span class="sxs-lookup"><span data-stu-id="ec697-167">-H</span></span>|<span data-ttu-id="ec697-168">R</span><span class="sxs-lookup"><span data-stu-id="ec697-168">R</span></span>|<span data-ttu-id="ec697-169">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="ec697-169">"ComputerName"</span></span>|  
|<span data-ttu-id="ec697-170">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="ec697-170">SQLCMDDBNAME</span></span>|<span data-ttu-id="ec697-171">-d</span><span class="sxs-lookup"><span data-stu-id="ec697-171">-d</span></span>|<span data-ttu-id="ec697-172">R</span><span class="sxs-lookup"><span data-stu-id="ec697-172">R</span></span>|<span data-ttu-id="ec697-173">""</span><span class="sxs-lookup"><span data-stu-id="ec697-173">""</span></span>|  
|<span data-ttu-id="ec697-174">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec697-174">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="ec697-175">-l</span><span class="sxs-lookup"><span data-stu-id="ec697-175">-l</span></span>|<span data-ttu-id="ec697-176">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-176">R/W</span></span>|<span data-ttu-id="ec697-177">"8" (秒)</span><span class="sxs-lookup"><span data-stu-id="ec697-177">"8" (seconds)</span></span>|  
|<span data-ttu-id="ec697-178">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec697-178">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="ec697-179">-t</span><span class="sxs-lookup"><span data-stu-id="ec697-179">-t</span></span>|<span data-ttu-id="ec697-180">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-180">R/W</span></span>|<span data-ttu-id="ec697-181">"0" = 無制限に待機</span><span class="sxs-lookup"><span data-stu-id="ec697-181">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="ec697-182">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="ec697-182">SQLCMDHEADERS</span></span>|<span data-ttu-id="ec697-183">-H</span><span class="sxs-lookup"><span data-stu-id="ec697-183">-h</span></span>|<span data-ttu-id="ec697-184">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-184">R/W</span></span>|<span data-ttu-id="ec697-185">"0"</span><span class="sxs-lookup"><span data-stu-id="ec697-185">"0"</span></span>|  
|<span data-ttu-id="ec697-186">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="ec697-186">SQLCMDCOLSEP</span></span>|<span data-ttu-id="ec697-187">-S</span><span class="sxs-lookup"><span data-stu-id="ec697-187">-s</span></span>|<span data-ttu-id="ec697-188">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-188">R/W</span></span>|<span data-ttu-id="ec697-189">" "</span><span class="sxs-lookup"><span data-stu-id="ec697-189">" "</span></span>|  
|<span data-ttu-id="ec697-190">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="ec697-190">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="ec697-191">-w</span><span class="sxs-lookup"><span data-stu-id="ec697-191">-w</span></span>|<span data-ttu-id="ec697-192">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-192">R/W</span></span>|<span data-ttu-id="ec697-193">"0"</span><span class="sxs-lookup"><span data-stu-id="ec697-193">"0"</span></span>|  
|<span data-ttu-id="ec697-194">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="ec697-194">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="ec697-195">-a</span><span class="sxs-lookup"><span data-stu-id="ec697-195">-a</span></span>|<span data-ttu-id="ec697-196">R</span><span class="sxs-lookup"><span data-stu-id="ec697-196">R</span></span>|<span data-ttu-id="ec697-197">"4096"</span><span class="sxs-lookup"><span data-stu-id="ec697-197">"4096"</span></span>|  
|<span data-ttu-id="ec697-198">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="ec697-198">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="ec697-199">-M</span><span class="sxs-lookup"><span data-stu-id="ec697-199">-m</span></span>|<span data-ttu-id="ec697-200">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-200">R/W</span></span>|<span data-ttu-id="ec697-201">"0"</span><span class="sxs-lookup"><span data-stu-id="ec697-201">"0"</span></span>|  
|<span data-ttu-id="ec697-202">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="ec697-202">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="ec697-203">-y</span><span class="sxs-lookup"><span data-stu-id="ec697-203">-y</span></span>|<span data-ttu-id="ec697-204">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-204">R/W</span></span>|<span data-ttu-id="ec697-205">"256"</span><span class="sxs-lookup"><span data-stu-id="ec697-205">"256"</span></span>|  
|<span data-ttu-id="ec697-206">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="ec697-206">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="ec697-207">-y</span><span class="sxs-lookup"><span data-stu-id="ec697-207">-Y</span></span>|<span data-ttu-id="ec697-208">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-208">R/W</span></span>|<span data-ttu-id="ec697-209">"0" = 無制限</span><span class="sxs-lookup"><span data-stu-id="ec697-209">"0" = unlimited</span></span>|  
|<span data-ttu-id="ec697-210">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="ec697-210">SQLCMDEDITOR</span></span>||<span data-ttu-id="ec697-211">R/W</span><span class="sxs-lookup"><span data-stu-id="ec697-211">R/W</span></span>|<span data-ttu-id="ec697-212">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="ec697-212">"edit.com"</span></span>|  
|<span data-ttu-id="ec697-213">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="ec697-213">SQLCMDINI</span></span>||<span data-ttu-id="ec697-214">R</span><span class="sxs-lookup"><span data-stu-id="ec697-214">R</span></span>|<span data-ttu-id="ec697-215">""</span><span class="sxs-lookup"><span data-stu-id="ec697-215">""</span></span>|  
  
 <span data-ttu-id="ec697-216">\*SQLCMDUSER、SQLCMDUSER、および SQLCMDUSER は、 **: Connect**が使用されるときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-216">\* SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect** is used.</span></span>  
  
 <span data-ttu-id="ec697-217">R は、その値がプログラムの初期化時に一度だけ設定できることを示します。</span><span class="sxs-lookup"><span data-stu-id="ec697-217">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="ec697-218">R/W は、 **setvar** コマンドを使用して値を再設定できること、および後続のコマンドで新しい値が使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="ec697-218">R/W indicates that the value can be reset by using the **setvar** command and subsequent commands will use the new value.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ec697-219">例</span><span class="sxs-lookup"><span data-stu-id="ec697-219">Examples</span></span>  
  
### <a name="a-using-the-setvar-command-in-a-script"></a><span data-ttu-id="ec697-220">A.</span><span class="sxs-lookup"><span data-stu-id="ec697-220">A.</span></span> <span data-ttu-id="ec697-221">スクリプトでの setvar コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="ec697-221">Using the setvar command in a script</span></span>  
 <span data-ttu-id="ec697-222">多くの **sqlcmd** オプションは、スクリプトで **setvar** コマンドを使用して制御できます。</span><span class="sxs-lookup"><span data-stu-id="ec697-222">Many **sqlcmd** options can be controlled in a script by using the **setvar** command.</span></span> <span data-ttu-id="ec697-223">次の例では、スクリプト `test.sql` が作成されます。このスクリプトでは、変数 `SQLCMDLOGINTIMEOUT` が `60` 秒に設定され、別のスクリプト変数 `server`が `testserver`に設定されています。</span><span class="sxs-lookup"><span data-stu-id="ec697-223">In the following example, the script `test.sql` is created in which the `SQLCMDLOGINTIMEOUT` variable is set to `60` seconds and another scripting variable, `server`, is set to `testserver`.</span></span> <span data-ttu-id="ec697-224">`test.sql`のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ec697-224">The following code is in `test.sql`.</span></span>  
  
 `:setvar SQLCMDLOGINTIMEOUT 60`  
  
 `:setvar server "testserver"`  
  
 `:connect $(server) -l $(SQLCMDLOGINTIMEOUT)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `The script is then called by using sqlcmd:`  
  
 `sqlcmd -i c:\test.sql`  
  
### <a name="b-using-the-setvar-command-interactively"></a><span data-ttu-id="ec697-225">B.</span><span class="sxs-lookup"><span data-stu-id="ec697-225">B.</span></span> <span data-ttu-id="ec697-226">setvar コマンドの対話的な使用</span><span class="sxs-lookup"><span data-stu-id="ec697-226">Using the setvar command interactively</span></span>  
 <span data-ttu-id="ec697-227">次の例では、 `setvar` コマンドを使用してスクリプト変数を対話的に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ec697-227">The following example shows how to set a scripting variable interactively by using the `setvar` command.</span></span>  
  
 `sqlcmd`  
  
 `:setvar  MYDATABASE AdventureWorks2012`  
  
 `USE $(MYDATABASE);`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'`  
  
 `1>`  
  
### <a name="c-using-command-prompt-environment-variables-within-sqlcmd"></a><span data-ttu-id="ec697-228">C.</span><span class="sxs-lookup"><span data-stu-id="ec697-228">C.</span></span> <span data-ttu-id="ec697-229">sqlcmd 内でのコマンド プロンプト環境変数の使用</span><span class="sxs-lookup"><span data-stu-id="ec697-229">Using command prompt environment variables within sqlcmd</span></span>  
 <span data-ttu-id="ec697-230">次の例では、4 つの環境変数を設定した後、 `are` から呼び出します。 `sqlcmd`</span><span class="sxs-lookup"><span data-stu-id="ec697-230">In the following example, four environment variables `are` set and then called from `sqlcmd`.</span></span>  
  
 `C:\>SET tablename=Person.Person`  
  
 `C:\>SET col1=FirstName`  
  
 `C:\>SET col2=LastName`  
  
 `C:\>SET title=Ms.`  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> SELECT TOP 5 $(col1) + ' ' + $(col2) AS Name`  
  
 `2> FROM $(tablename)`  
  
 `3> WHERE Title ='$(title)'`  
  
 `4> GO`  
  
### <a name="d-using-user-level-environment-variables-within-sqlcmd"></a><span data-ttu-id="ec697-231">D.</span><span class="sxs-lookup"><span data-stu-id="ec697-231">D.</span></span> <span data-ttu-id="ec697-232">sqlcmd 内でのユーザーレベル環境変数の使用</span><span class="sxs-lookup"><span data-stu-id="ec697-232">Using user-level environment variables within sqlcmd</span></span>  
 <span data-ttu-id="ec697-233">次の例では、ユーザーレベル環境変数 `%Temp%` をコマンド プロンプトで設定し、 `sqlcmd` 入力ファイルに渡します。</span><span class="sxs-lookup"><span data-stu-id="ec697-233">In the following example the user-level environmental variable `%Temp%` is set at the command prompt and passed to the `sqlcmd` input file.</span></span> <span data-ttu-id="ec697-234">ユーザーレベル環境変数を取得するには、 **[コントロール パネル]** の **[システム]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec697-234">To obtain the user-level environment variable, in **Control Panel**, double-click **System**.</span></span> <span data-ttu-id="ec697-235">**[詳細設定]** タブをクリックし、 **[環境変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec697-235">Click the **Advance** tab, and then click **Environment Variables**.</span></span>  
  
 <span data-ttu-id="ec697-236">入力ファイル `c:\testscript.txt`のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ec697-236">The following code is in the input file `c:\testscript.txt`:</span></span>  
  
 `:OUT $(MyTempDirectory)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName`  
  
 `FROM AdventureWorks2012.Person.Person`  
  
 <span data-ttu-id="ec697-237">`WHERE BusinessEntityID` `< 5;`</span><span class="sxs-lookup"><span data-stu-id="ec697-237">`WHERE BusinessEntityID` `< 5;`</span></span>  
  
 <span data-ttu-id="ec697-238">コマンド プロンプトで、次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ec697-238">This following code is entered at the command prompt:</span></span>  
  
 `C:\ >SET MyTempDirectory=%Temp%\output.txt`  
  
 `C:\ >sqlcmd -i C:\testscript.txt`  
  
 <span data-ttu-id="ec697-239">出力ファイル C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt には、次の結果が送信されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-239">The following result is sent to the output file C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt.</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `FirstName`  
  
 `--------------------------------------------------`  
  
 `Gustavo`  
  
 `Catherine`  
  
 `Kim`  
  
 `Humberto`  
  
 `(4 rows affected)`  
  
### <a name="e-using-a-startup-script"></a><span data-ttu-id="ec697-240">E.</span><span class="sxs-lookup"><span data-stu-id="ec697-240">E.</span></span> <span data-ttu-id="ec697-241">スタートアップ スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="ec697-241">Using a startup script</span></span>  
 <span data-ttu-id="ec697-242">**sqlcmd** スタートアップ スクリプトは、 **sqlcmd** の起動時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-242">A **sqlcmd** startup script is executed when **sqlcmd** is started.</span></span> <span data-ttu-id="ec697-243">次の例では、環境変数 `SQLCMDINI`が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-243">The following example sets the environment variable `SQLCMDINI`.</span></span> <span data-ttu-id="ec697-244">以下の内容を次に示します: `init.sql.`</span><span class="sxs-lookup"><span data-stu-id="ec697-244">This is the contents of `init.sql.`</span></span>  
  
 `SET NOCOUNT ON`  
  
 `GO`  
  
 `DECLARE @nt_username nvarchar(128)`  
  
 `SET @nt_username = (SELECT rtrim(convert(nvarchar(128), nt_username))`  
  
 `FROM sys.dm_exec_sessions WHERE spid = @@SPID)`  
  
 `SELECT  @nt_username + ' is connected to ' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('servername'))) +`  
  
 `' (' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('productversion'))) +`  
  
 `')'`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH 100`  
  
 `SET NOCOUNT OFF`  
  
 `GO`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH`  
  
 <span data-ttu-id="ec697-245">次のコードにより、 `init.sql` の起動時に `sqlcmd` ファイルが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-245">This calls the `init.sql` file when `sqlcmd` is started.</span></span>  
  
 `C:\> SET sqlcmdini=c:\init.sql`  
  
 `>1 Sqlcmd`  
  
 <span data-ttu-id="ec697-246">出力結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ec697-246">This is the output.</span></span>  
  
 `>1 < user > is connected to < server > (9.00.2047.00)`  
  
> [!NOTE]  
>  <span data-ttu-id="ec697-247">**-X** オプションを使用すると、スタートアップ スクリプト機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ec697-247">The **-X** option disables the startup script feature.</span></span>  
  
### <a name="f-variable-expansion"></a><span data-ttu-id="ec697-248">F.</span><span class="sxs-lookup"><span data-stu-id="ec697-248">F.</span></span> <span data-ttu-id="ec697-249">変数の拡張</span><span class="sxs-lookup"><span data-stu-id="ec697-249">Variable expansion</span></span>  
 <span data-ttu-id="ec697-250">次の例では、 **sqlcmd** 変数の形式でデータを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ec697-250">The following example shows working with data in the form of a **sqlcmd** variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `CREATE TABLE AdventureWorks2012.dbo.VariableTest`  
  
 `(`  
  
 `Col1 nvarchar(50)`  
  
 `);`  
  
 `GO`  
  
 <span data-ttu-id="ec697-251">`Col1` の `dbo.VariableTest` に、値 `$(tablename)`を含む 1 行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ec697-251">Insert one row into `Col1` of `dbo.VariableTest` that contains the value `$(tablename)`.</span></span>  
  
 `INSERT INTO AdventureWorks2012.dbo.VariableTest(Col1)`  
  
 `VALUES('$(tablename)');`  
  
 `GO`  
  
 <span data-ttu-id="ec697-252">`sqlcmd` プロンプトで、 `$(tablename)`に変数を設定していない場合、次のステートメントでは行が返されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-252">At the `sqlcmd` prompt, when no variable is set equal to `$(tablename)`, the following statements return the row.</span></span>  
  
 `C:\> sqlcmd`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>2 GO`  
  
 `>3 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>4 GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `>1 Col1`  
  
 `>2 ------------------`  
  
 `>3 $(tablename)`  
  
 `>4`  
  
 `>5 (1 rows affected)`  
  
 <span data-ttu-id="ec697-253">変数 `MyVar` が `$(tablename)`に設定されている場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ec697-253">Given the variable `MyVar` is set to `$(tablename)`.</span></span>  
  
 `>6 :setvar MyVar $(tablename)`  
  
 <span data-ttu-id="ec697-254">次のステートメントでは、行だけでなく、"'tablename' スクリプト変数が定義されていません。" というメッセージも返されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-254">These statements return the row and also return the message "'tablename' scripting variable not defined."</span></span>  
  
 `>6 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>7 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>2 GO`  
  
 <span data-ttu-id="ec697-255">次のステートメントでは行が返されます。</span><span class="sxs-lookup"><span data-stu-id="ec697-255">These statements return the row.</span></span>  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(MyVar)';`  
  
 `>2 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(MyVar)';`  
  
 `>2 GO`  
  
## <a name="see-also"></a><span data-ttu-id="ec697-256">参照</span><span class="sxs-lookup"><span data-stu-id="ec697-256">See Also</span></span>  
 <span data-ttu-id="ec697-257">[sqlcmd ユーティリティの使用](sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ec697-257">[Use the sqlcmd Utility](sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="ec697-258">[sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ec697-258">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="ec697-259">コマンド プロンプト ユーティリティ リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="ec697-259">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](../../tools/command-prompt-utility-reference-database-engine.md)  
  
  
