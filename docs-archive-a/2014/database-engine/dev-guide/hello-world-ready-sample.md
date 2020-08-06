---
title: Hello World 準備完了のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 1cb94266-f702-4a57-a1ae-689a89c98757
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7cc3088af258962a4cec615214147d1f4f09c431
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742510"
---
# <a name="hello-world-ready-sample"></a><span data-ttu-id="7aedd-102">Hello World Ready サンプル</span><span class="sxs-lookup"><span data-stu-id="7aedd-102">Hello World Ready Sample</span></span>
  <span data-ttu-id="7aedd-103">Hello World Ready サンプルでは、国際化対応の、CLR (共通言語ランタイム) 統合ベースの単純なストアド プロシージャの作成、配置、およびテストにかかわる基本的な操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="7aedd-103">The Hello World Ready sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple world ready common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="7aedd-104">国際化対応コンポーネントは、コンポーネントのソース コードを変更することなく、世界中の市場に向けて、異なる言語へのローカライズを簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-104">A world-ready component can be easily localized into different languages for different markets around the world without changing the component's source code.</span></span> <span data-ttu-id="7aedd-105">また、このサンプルでは、ストアド プロシージャによって動的に構築されてクライアントに返されるレコードおよび出力パラメーターを使用してデータを返す方法についても示します。このサンプルは、Hello World サンプルとほぼ同じですが、このアプリケーションのローカライズをより簡単かつ安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-105">This sample also demonstrates how to return data through an output parameter and through a record, which is dynamically constructed by the stored procedure and returned to the client.This sample is almost identical to the Hello World Sample except that it is much easier and safer to localize this application.</span></span> <span data-ttu-id="7aedd-106">ローカライズ済みテキストを変更するには、次の作業を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-106">To change localized text requires the following:</span></span>  
  
1.  <span data-ttu-id="7aedd-107">XML ファイルの変更 (.`resx`</span><span class="sxs-lookup"><span data-stu-id="7aedd-107">Changing an XML file (the .`resx`</span></span> <span data-ttu-id="7aedd-108">ファイル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7aedd-108">file) for the particular culture in the resources directory</span></span>  
  
2.  <span data-ttu-id="7aedd-109">`resgen` を使用して、カルチャに応じたリソース ファイルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-109">Building the culture's resources file by using `resgen`</span></span>  
  
3.  <span data-ttu-id="7aedd-110">そのカルチャに関して更新されたサテライト DLL をビルドします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-110">Building the updated satellite DLL for that culture</span></span>  
  
4.  <span data-ttu-id="7aedd-111">このアセンブリを SQL Server でいったん削除してから、追加します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-111">Dropping and adding that assembly in SQL Server</span></span>  
  
 <span data-ttu-id="7aedd-112">CLR ストアド プロシージャ自体のソース コードおよびアセンブリは変更されません。</span><span class="sxs-lookup"><span data-stu-id="7aedd-112">The source code and assembly for the CLR stored procedure itself does not change.</span></span> <span data-ttu-id="7aedd-113">リソース アセンブリのコンパイル方法とリンク方法を示す `build.cmd` スクリプトが用意されています。アプリケーションのソース コードによって、現在実行しているアセンブリに基づいたリソース マネージャーが作成されますが、ストアド プロシージャを含む DLL にカルチャ ニュートラル リソースを埋め込む必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7aedd-113">A `build.cmd` script is provided which demonstrates how to compile and link the resource assemblies.Although the source code for the application creates a resource manager based the currently executing assembly, you do not have to embed the culture neutral resources in the DLL that contains the stored procedure.</span></span> <span data-ttu-id="7aedd-114">`System.Resources.NeutralResourcesLanguage attribute` によって、カルチャ ニュートラル リソースがサテライト DLL に存在することが許可されます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-114">The `System.Resources.NeutralResourcesLanguage attribute` permits the culture-neutral resources to exist in a satellite DLL.</span></span> <span data-ttu-id="7aedd-115">この目的でそれぞれ別の DLL を使用すると、ローカライズ済みテキストの追加や変更が必要な場合でも、CLR ストアド プロシージャを含んでいるプライマリ DLL の変更が必要なくなるため非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="7aedd-115">It is much better to use a separate DLL for this purpose so that when localized text needs to be added or changed, the primary DLL that contains the CLR stored procedure does not have to be changed.</span></span> <span data-ttu-id="7aedd-116">これは、型の削除と再追加を困難にするような列やその他の依存関係を含んでいることのある、CLR ユーザー定義型には特に役立ちます。通常、サテライト DLL バージョンはメイン アセンブリ バージョンと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-116">This is especially useful for CLR user-defined types that might have columns and other dependencies which would make it difficult to drop and re-add the type.Ordinarily, the satellite DLL versions must be identical to the main assembly version.</span></span> <span data-ttu-id="7aedd-117">ただし、`SatelliteContractVersion` 属性を使用して、サテライト アセンブリを更新せずにメイン アセンブリの更新を許可することもできます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-117">However, you can use the `SatelliteContractVersion` attribute to allow the main assembly to be updated without updating the satellite assemblies too.</span></span> <span data-ttu-id="7aedd-118">詳細については、Microsoft .NET のドキュメントで `ResourceManager` クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7aedd-118">For more information, see the `ResourceManager` class in the Microsoft .NET documentation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7aedd-119">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="7aedd-119">Prerequisites</span></span>  
 <span data-ttu-id="7aedd-120">このサンプルは、SQL Server 2005 以降のバージョンでのみ動作します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-120">This sample works only with SQL Server 2005 and later versions.</span></span>  
  
 <span data-ttu-id="7aedd-121">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-121">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="7aedd-122">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="7aedd-122">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="7aedd-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/sql-server/sql-server-editions-express)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-123">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="7aedd-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://go.microsoft.com/fwlink/?linkid=62796)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="7aedd-124">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="7aedd-125">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="7aedd-125">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="7aedd-126">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-126">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="7aedd-127">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-127">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="7aedd-128">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-128">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="7aedd-129">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7aedd-129">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="7aedd-130">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="7aedd-130">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="7aedd-131">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-131">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="7aedd-132">CLR を有効にするには、 `ALTER SETTINGS` サーバーレベルの権限が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-132">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="7aedd-133">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-133">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="7aedd-134">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの管理者でない場合は、インストールを完了するために **CreateAssembly** 権限が管理者から付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7aedd-134">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="7aedd-135">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="7aedd-135">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="7aedd-136">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-136">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="7aedd-137">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="7aedd-137">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="7aedd-138">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-138">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="7aedd-139">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-139">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="7aedd-140">c:\MySample で、`HelloWorld.vb` (Visual Basic サンプル) または `HelloWorld.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-140">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="7aedd-141">C:\MySample で、ファイルを作成 `messages.resx` し、サンプルコードをファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-141">In c:\MySample, create the file `messages.resx` and copy the sample code into the file.</span></span>  
  
5.  <span data-ttu-id="7aedd-142">C:\MySample で、 `messages.de.resx` `messages.resx` `messages.de.resx` 行を変更した後にファイルを保存してファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-142">In c:\MySample, create the file `messages.de.resx` by saving the file `messages.resx` as `messages.de.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7aedd-143">次のように変更</span><span class="sxs-lookup"><span data-stu-id="7aedd-143">To read</span></span>  
  
    -   `<value xml:space="preserve">Hallo Welt!</value>`  
  
6.  <span data-ttu-id="7aedd-144">C:\MySample で、 `messages.es.resx` `messages.resx` `messages.es.resx` 行を変更した後にファイルを保存してファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-144">In c:\MySample, create the file `messages.es.resx` by saving the file `messages.resx` as `messages.es.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7aedd-145">次のように変更</span><span class="sxs-lookup"><span data-stu-id="7aedd-145">To read</span></span>  
  
    -   `<value xml:space="preserve">Hola a todos</value>`  
  
7.  <span data-ttu-id="7aedd-146">C:\MySample で、 `messages.fr.resx` `messages.resx` `messages.fr.resx` 行を変更した後にファイルを保存してファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-146">In c:\MySample, create the file `messages.fr.resx` by saving the file `messages.resx` as `messages.fr.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7aedd-147">次のように変更</span><span class="sxs-lookup"><span data-stu-id="7aedd-147">To read</span></span>  
  
    -   `<value xml:space="preserve">BonjourÂ !</value>`  
  
8.  <span data-ttu-id="7aedd-148">C:\MySample で、 `messages.fr-FR.resx` `messages.resx` `messages.fr-FR.resx` 行を変更した後にファイルを保存してファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-148">In c:\MySample, create the file `messages.fr-FR.resx` by saving the file `messages.resx` as `messages.fr-FR.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7aedd-149">次のように変更</span><span class="sxs-lookup"><span data-stu-id="7aedd-149">To read</span></span>  
  
    -   `<value xml:space="preserve">Bonjour de France!</value>`  
  
9. <span data-ttu-id="7aedd-150">C:\MySample で、 `messages.it.resx` `messages.resx` `messages.it.resx` 行を変更した後にファイルを保存してファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-150">In c:\MySample, create the file `messages.it.resx` by saving the file `messages.resx` as `messages.it.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7aedd-151">次のように変更</span><span class="sxs-lookup"><span data-stu-id="7aedd-151">To read</span></span>  
  
    -   `<value xml:space="preserve">Buongiorno</value>`  
  
10. <span data-ttu-id="7aedd-152">C:\MySample で、 `messages.ja.resx` `messages.resx` `messages.ja.resx` 行を変更した後にファイルを保存してファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-152">In c:\MySample, create the file `messages.ja.resx` by saving the file `messages.resx` as `messages.ja.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="7aedd-153">次のように変更</span><span class="sxs-lookup"><span data-stu-id="7aedd-153">To read</span></span>  
  
    -   <span data-ttu-id="7aedd-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span><span class="sxs-lookup"><span data-stu-id="7aedd-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span></span>  
  
11. <span data-ttu-id="7aedd-155">c:\MySample で、ファイル `build.com` を作成し、サンプル コードをこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-155">In c:\MySample, create the file `build.com` and copy the sample code into the file</span></span>  
  
12. <span data-ttu-id="7aedd-156">ビルドされたファイルをコマンド プロンプトで実行して、サテライト アセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-156">Build the satellite assembles by executing the file build at the command prompt.</span></span>  
  
13. <span data-ttu-id="7aedd-157">次のいずれかをコマンド プロンプトで実行して、サンプル コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-157">Compile the sample code from the command line prompt by executing the one of the following:</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /out:HelloWorldReady.dll /target:library HelloWorld.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:HelloWorldReady.dll /target:library Hello.csCopy the tsql installation code into a file and save it as Install.sql in the sample directory.`  
  
14. <span data-ttu-id="7aedd-158">サンプルが `C:\MySample\`以外のディレクトリにインストールされている場合は、その場所を示すように、ファイル `Install.sql` を編集します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-158">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
15. <span data-ttu-id="7aedd-159">次のコマンドを実行して、アセンブリとストアド プロシージャを配置します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-159">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
16. <span data-ttu-id="7aedd-160">[!INCLUDE[tsql](../../includes/tsql-md.md)]テストコマンドスクリプトをファイルにコピーし、として `test.sql` サンプルディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-160">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
17. <span data-ttu-id="7aedd-161">次のコマンドを使用してテスト スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-161">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
18. <span data-ttu-id="7aedd-162">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-162">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
19. <span data-ttu-id="7aedd-163">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-163">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="7aedd-164">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="7aedd-164">Sample Code</span></span>  
 <span data-ttu-id="7aedd-165">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-165">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="7aedd-166">C#</span><span class="sxs-lookup"><span data-stu-id="7aedd-166">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Globalization;  
using System.Threading;  
using System.Resources;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
[assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)]  
[assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance, System.Runtime.ConstrainedExecution.Cer.None)]  
  
    public sealed partial class StoredProcedures  
    {  
        private StoredProcedures()  
        {  
        }  
  
        [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1021:AvoidOutParameters"), Microsoft.SqlServer.Server.SqlProcedure]  
        public static void HelloWorldReady(string culture, out string greeting)  
        {  
ResourceManager rm   
= new ResourceManager("Messages",   
Assembly.GetExecutingAssembly());  
  
string message = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture));  
  
            Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 24);  
            SqlDataRecord greetingRecord  
                = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
            greetingRecord.SetString(0, message);  
            SqlContext.Pipe.Send(greetingRecord);  
            greeting = message;  
        }  
    }  
  
```  
  
 <span data-ttu-id="7aedd-167">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7aedd-167">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Globalization  
Imports System.Resources  
Imports System.Reflection  
Imports System.Runtime.InteropServices  
<Assembly: AssemblyVersion("1.0.*")>   
<Assembly: System.Runtime.InteropServices.ComVisible(False)>   
<Assembly: System.CLSCompliant(True)>   
<Assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)>   
<Assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)>   
<Assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState, Runtime.ConstrainedExecution.Cer.None)>   
  
Partial Public NotInheritable Class StoredProcedures  
    Private Sub New()  
    End Sub  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorldReady(ByVal culture As String, ByRef greeting As String)  
        Dim rm As New ResourceManager("Messages", Assembly.GetExecutingAssembly())  
        Dim message As String = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture))  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 24)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, message)  
        SqlContext.Pipe.Send(greetingRecord)  
        greeting = message  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="7aedd-168">次の `build.com` は、サテライト アセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-168">This is `build.com`, which builds the satellite assemblies.</span></span>  
  
```  
resgen Messages.resx  
resgen Messages.de.resx  
resgen Messages.es.resx  
resgen Messages.fr.resx  
resgen Messages.fr-Fr.resx  
resgen Messages.it.resx  
resgen Messages.ja.resx  
if not exist de/ mkdir de  
if not exist es/ mkdir es  
if not exist fr/ mkdir fr  
if not exist fr-FR/ mkdir fr-FR  
if not exist it/ mkdir it  
if not exist ja/ mkdir ja  
al /t:lib /culture:de /embed:Messages.de.resources /out:de\HelloWorldReady.resources.dll  
al /t:lib /culture:es /embed:Messages.es.resources /out:es\HelloWorldReady.resources.dll  
al /t:lib /culture:fr /embed:Messages.fr.resources /out:fr\HelloWorldReady.resources.dll  
al /t:lib /culture:fr-FR /embed:Messages.fr-FR.resources /out:fr-FR\HelloWorldReady.resources.dll  
al /t:lib /culture:it /embed:Messages.it.resources /out:it\HelloWorldReady.resources.dll  
al /t:lib /culture:ja /embed:Messages.ja.resources /out:ja\HelloWorldReady.resources.dll  
al /t:lib /culture:"" /embed:Messages.resources /out:HelloWorldReady.resources.dll  
```  
  
 <span data-ttu-id="7aedd-169">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを配置し、データベース内にストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-169">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assemblies and creates the stored procedure within the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = N'C:\MySample\'  
  
-- Add the assembly and CLR integration based stored procedure  
  
CREATE ASSEMBLY HelloWorldReady  
FROM @SamplesPath + 'HelloWorldReady.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.neutral]  
FROM @SamplesPath + 'HelloWorldReady.resources.dll'  
WITH permission_set = Safe;   
  
CREATE ASSEMBLY [HelloWorldReady.resources.de]  
FROM @SamplesPath + '\de\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.es]  
FROM @SamplesPath + '\es\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr]  
FROM @SamplesPath + '\fr\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr-FR]  
FROM @SamplesPath + '\fr-FR\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.it]  
FROM @SamplesPath + '\it\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.ja]  
FROM @SamplesPath + '\ja\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorldReady  
(  
@Culture NVarchar(12),  
@Greeting NVarchar(24) OUTPUT  
)  
AS EXTERNAL NAME HelloWorldReady.StoredProcedures.HelloWorldReady;  
GO  
  
USE master;  
GO  
```  
  
 <span data-ttu-id="7aedd-170">次の `test.sql` は、各ロケールで関数を実行してサンプルをテストします。</span><span class="sxs-lookup"><span data-stu-id="7aedd-170">This is `test.sql`, which tests the sample by executing the functions on each locale.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
DECLARE @GreetingDe nvarchar(24);  
DECLARE @GreetingDe_CH nvarchar(24);  
DECLARE @GreetingEn nvarchar(24);  
DECLARE @GreetingEs nvarchar(24);  
DECLARE @GreetingFr nvarchar(24);  
DECLARE @GreetingFr_FR nvarchar(24);  
DECLARE @GreetingIt nvarchar(24);  
DECLARE @GreetingJa nvarchar(24);  
  
--German as spoken anywhere in the world (the neutral German culture)  
EXEC usp_HelloWorldReady 'de', @GreetingDe OUTPUT;  
--German as spoken in Switzerland.  Because we don't have a specific assembly  
--for this case, the .NET Framework will automatically fall back to the neutral German culture DLL.  
EXEC usp_HelloWorldReady 'de-CH', @GreetingDe_CH OUTPUT;  
EXEC usp_HelloWorldReady 'en', @GreetingEn OUTPUT;  
EXEC usp_HelloWorldReady 'es', @GreetingEs OUTPUT;  
--French as spoken anywhere in the world (the neutral French culture)  
EXEC usp_HelloWorldReady 'fr', @GreetingFr OUTPUT  
--French as spoken in France.  Since we do have a specific assembly for this case, a specific   
--greeting is provided from that DLL.  The neutral French culture DLL is not used in this case.  
EXEC usp_HelloWorldReady 'fr-FR', @GreetingFr_FR OUTPUT  
EXEC usp_HelloWorldReady 'it', @GreetingIt OUTPUT;  
EXEC usp_HelloWorldReady 'ja', @GreetingJa OUTPUT;  
  
SELECT @GreetingDe AS OUTPUT_PARAMETER_DE;  
SELECT @GreetingDe_CH AS OUTPUT_PARAMETER_De_CH;  
SELECT @GreetingEn AS OUTPUT_PARAMETER_EN;  
SELECT @GreetingEs AS OUTPUT_PARAMETER_ES;  
SELECT @GreetingFr AS OUTPUT_PARAMETER_FR;  
SELECT @GreetingFr_FR AS OUTPUT_PARAMETER_Fr_FR;  
SELECT @GreetingIt AS OUTPUT_PARAMETER_IT;  
SELECT @GreetingJa AS OUTPUT_PARAMETER_JA;  
  
GO  
```  
  
 <span data-ttu-id="7aedd-171">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、データベースからアセンブリとストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="7aedd-171">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assemblies and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
USE master;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7aedd-172">参照</span><span class="sxs-lookup"><span data-stu-id="7aedd-172">See Also</span></span>  
 [<span data-ttu-id="7aedd-173">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="7aedd-173">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
