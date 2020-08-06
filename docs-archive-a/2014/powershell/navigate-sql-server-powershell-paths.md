---
title: SQL Server PowerShell パスの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a605479991c3e907cd9dcae254cc1bc04a49392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741098"
---
# <a name="navigate-sql-server-powershell-paths"></a><span data-ttu-id="49002-102">SQL Server PowerShell パスの移動</span><span class="sxs-lookup"><span data-stu-id="49002-102">Navigate SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="49002-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell プロバイダーは、ファイル パスと同様の構造で、SQL Server のインスタンス内のオブジェクトのセットを公開します。</span><span class="sxs-lookup"><span data-stu-id="49002-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell provider exposes the set of objects in an instance of SQL Server in a structure similar to a file path.</span></span> <span data-ttu-id="49002-104">Windows PowerShell コマンドレットを使用することで、プロバイダー パスを移動し、カスタム ドライブを作成して、入力するパスを短くすることができます。</span><span class="sxs-lookup"><span data-stu-id="49002-104">You can use Windows PowerShell cmdlets to navigate the provider path, and create custom drives to shorten the path you have to type.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="49002-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="49002-105">Before You Begin</span></span>  
 <span data-ttu-id="49002-106">Windows PowerShell では、コマンドレットを実装して、PowerShell プロバイダーによりサポートされるオブジェクトの階層を表すパス構造を移動できます。</span><span class="sxs-lookup"><span data-stu-id="49002-106">Windows PowerShell implements cmdlets to navigate the path structure that represent the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="49002-107">そのパス内のノードへ移動したときに、他のコマンドレットを使用して、現在のオブジェクトの基本的な操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="49002-107">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span> <span data-ttu-id="49002-108">コマンドレットは頻繁に使用されるため、短い標準の別名が用意されています。</span><span class="sxs-lookup"><span data-stu-id="49002-108">Because the cmdlets are used frequently, they have short, canonical aliases.</span></span> <span data-ttu-id="49002-109">また、コマンドレットを類似のコマンド プロンプトのコマンドにマップする別名のセットと、UNIX シェル コマンド用の別のセットもあります。</span><span class="sxs-lookup"><span data-stu-id="49002-109">There is also one set of aliases that maps the cmdlets to similar command prompt commands, and another set for UNIX shell commands.</span></span>  
  
 <span data-ttu-id="49002-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーは、次の表に示すように、プロバイダーのコマンドレットのサブセットを実装します。</span><span class="sxs-lookup"><span data-stu-id="49002-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements a subset of the provider cmdlets, shown in the following table.</span></span>  
  
|<span data-ttu-id="49002-111">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="49002-111">cmdlet</span></span>|<span data-ttu-id="49002-112">標準の別名</span><span class="sxs-lookup"><span data-stu-id="49002-112">Canonical alias</span></span>|<span data-ttu-id="49002-113">コマンドの別名</span><span class="sxs-lookup"><span data-stu-id="49002-113">cmd alias</span></span>|<span data-ttu-id="49002-114">UNIX シェルの別名</span><span class="sxs-lookup"><span data-stu-id="49002-114">UNIX shell alias</span></span>|<span data-ttu-id="49002-115">[説明]</span><span class="sxs-lookup"><span data-stu-id="49002-115">Description</span></span>|  
|------------|---------------------|---------------|----------------------|-----------------|  
|<span data-ttu-id="49002-116">**Get-Location**</span><span class="sxs-lookup"><span data-stu-id="49002-116">**Get-Location**</span></span>|<span data-ttu-id="49002-117">**gl**</span><span class="sxs-lookup"><span data-stu-id="49002-117">**gl**</span></span>|<span data-ttu-id="49002-118">**pwd**</span><span class="sxs-lookup"><span data-stu-id="49002-118">**pwd**</span></span>|<span data-ttu-id="49002-119">**pwd**</span><span class="sxs-lookup"><span data-stu-id="49002-119">**pwd**</span></span>|<span data-ttu-id="49002-120">現在のノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="49002-120">Gets the current node.</span></span>|  
|`Set-Location`|<span data-ttu-id="49002-121">**法**</span><span class="sxs-lookup"><span data-stu-id="49002-121">**sl**</span></span>|<span data-ttu-id="49002-122">**cd、chdir**</span><span class="sxs-lookup"><span data-stu-id="49002-122">**cd, chdir**</span></span>|<span data-ttu-id="49002-123">**cd、chdir**</span><span class="sxs-lookup"><span data-stu-id="49002-123">**cd, chdir**</span></span>|<span data-ttu-id="49002-124">現在のノードを変更します。</span><span class="sxs-lookup"><span data-stu-id="49002-124">Changes the current node.</span></span>|  
|<span data-ttu-id="49002-125">**Get-ChildItem**</span><span class="sxs-lookup"><span data-stu-id="49002-125">**Get-ChildItem**</span></span>|<span data-ttu-id="49002-126">**gci**</span><span class="sxs-lookup"><span data-stu-id="49002-126">**gci**</span></span>|<span data-ttu-id="49002-127">**dir**</span><span class="sxs-lookup"><span data-stu-id="49002-127">**dir**</span></span>|<span data-ttu-id="49002-128">**avl**</span><span class="sxs-lookup"><span data-stu-id="49002-128">**ls**</span></span>|<span data-ttu-id="49002-129">現在のノードに格納されているオブジェクトの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="49002-129">Lists the objects stored at the current node.</span></span>|  
|<span data-ttu-id="49002-130">**Get-Item**</span><span class="sxs-lookup"><span data-stu-id="49002-130">**Get-Item**</span></span>|<span data-ttu-id="49002-131">**gi**</span><span class="sxs-lookup"><span data-stu-id="49002-131">**gi**</span></span>|||<span data-ttu-id="49002-132">現在のアイテムのプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="49002-132">Returns the properties of the current item.</span></span>|  
|<span data-ttu-id="49002-133">**Rename-Item**</span><span class="sxs-lookup"><span data-stu-id="49002-133">**Rename-Item**</span></span>|<span data-ttu-id="49002-134">**rni**</span><span class="sxs-lookup"><span data-stu-id="49002-134">**rni**</span></span>|<span data-ttu-id="49002-135">**rn**</span><span class="sxs-lookup"><span data-stu-id="49002-135">**rn**</span></span>|<span data-ttu-id="49002-136">**ren**</span><span class="sxs-lookup"><span data-stu-id="49002-136">**ren**</span></span>|<span data-ttu-id="49002-137">オブジェクトの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="49002-137">Renames an object.</span></span>|  
|<span data-ttu-id="49002-138">**Remove-Item**</span><span class="sxs-lookup"><span data-stu-id="49002-138">**Remove-Item**</span></span>|<span data-ttu-id="49002-139">**ri**</span><span class="sxs-lookup"><span data-stu-id="49002-139">**ri**</span></span>|<span data-ttu-id="49002-140">**del、rd**</span><span class="sxs-lookup"><span data-stu-id="49002-140">**del, rd**</span></span>|<span data-ttu-id="49002-141">**rm、rmdir**</span><span class="sxs-lookup"><span data-stu-id="49002-141">**rm, rmdir**</span></span>|<span data-ttu-id="49002-142">オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="49002-142">Removes an object.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="49002-143">一部の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子 (オブジェクト名) には、Windows PowerShell のパス名ではサポートされない文字が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="49002-143">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers (object names) contain characters that Windows PowerShell does not support in path names.</span></span> <span data-ttu-id="49002-144">それらの文字を含む名前の使用方法の詳細については、「 [PowerShell での SQL Server 識別子](sql-server-identifiers-in-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49002-144">For more information about how to use names that contain these characters, see [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).</span></span>  
  
### <a name="sql-server-information-returned-by-get-childitem"></a><span data-ttu-id="49002-145">Get-childitem によって返される SQL Server 情報</span><span class="sxs-lookup"><span data-stu-id="49002-145">SQL Server Information Returned by Get-ChildItem</span></span>  
 <span data-ttu-id="49002-146">**Get-ChildItem** (またはその別名の **dir** および **ls** ) で返される情報は、SQLSERVER: パス内の場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="49002-146">The information returned by **Get-ChildItem** (or its **dir** and **ls** aliases) depends on your location in a SQLSERVER: path.</span></span>  
  
|<span data-ttu-id="49002-147">パスの場所</span><span class="sxs-lookup"><span data-stu-id="49002-147">Path location</span></span>|<span data-ttu-id="49002-148">Get-ChildItem の結果</span><span class="sxs-lookup"><span data-stu-id="49002-148">Get-ChildItem results</span></span>|  
|-------------------|----------------------------|  
|<span data-ttu-id="49002-149">SQLSERVER:\SQL</span><span class="sxs-lookup"><span data-stu-id="49002-149">SQLSERVER:\SQL</span></span>|<span data-ttu-id="49002-150">ローカル コンピューターの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="49002-150">Returns the name of the local computer.</span></span> <span data-ttu-id="49002-151">SMO または WMI を使用して他のコンピューター上の [!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスに接続している場合は、それらのコンピューターも一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="49002-151">If you have used the SMO or WMI to connect to instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on other computers, those computers are also listed.</span></span>|  
|<span data-ttu-id="49002-152">SQLSERVER: \ SQL \\ *ComputerName*</span><span class="sxs-lookup"><span data-stu-id="49002-152">SQLSERVER:\SQL\\*ComputerName*</span></span>|<span data-ttu-id="49002-153">コンピューター上の [!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスの一覧。</span><span class="sxs-lookup"><span data-stu-id="49002-153">The list of instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on the computer.</span></span>|  
|<span data-ttu-id="49002-154">SQLSERVER: \ SQL \\ *ComputerName* \\ *InstanceName*</span><span class="sxs-lookup"><span data-stu-id="49002-154">SQLSERVER:\SQL\\*ComputerName*\\*InstanceName*</span></span>|<span data-ttu-id="49002-155">インスタンス内の最上位レベルのオブジェクトの種類の一覧 (Endpoints、Certificates、Databases など)。</span><span class="sxs-lookup"><span data-stu-id="49002-155">The list of top-level object types in the instance, such as Endpoints, Certificates, and Databases.</span></span>|  
|<span data-ttu-id="49002-156">オブジェクト クラスのノード (Databases など)</span><span class="sxs-lookup"><span data-stu-id="49002-156">Object class node, such as Databases</span></span>|<span data-ttu-id="49002-157">その種類のオブジェクトの一覧 (データベースの場合は master、model、AdventureWorks2008R2 など)。</span><span class="sxs-lookup"><span data-stu-id="49002-157">The list of objects of that type, such as the list of databases: master, model, AdventureWorks20008R2.</span></span>|  
|<span data-ttu-id="49002-158">オブジェクト名のノード (AdventureWorks2012 など)</span><span class="sxs-lookup"><span data-stu-id="49002-158">Object name node, such as AdventureWorks2012</span></span>|<span data-ttu-id="49002-159">オブジェクト内に格納されているオブジェクトの種類の一覧。</span><span class="sxs-lookup"><span data-stu-id="49002-159">The list of object types contained within the object.</span></span> <span data-ttu-id="49002-160">たとえば、データベースの場合はテーブルやビューなどのオブジェクトの種類が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="49002-160">For example, a database would list object types such as tables and views.</span></span>|  
  
 <span data-ttu-id="49002-161">既定では、 **Get-ChildItem** でシステム オブジェクトは一覧表示されません。</span><span class="sxs-lookup"><span data-stu-id="49002-161">By default, **Get-ChildItem** does not list any system objects.</span></span> <span data-ttu-id="49002-162">システム オブジェクト (たとえば *sys* スキーマ内のオブジェクト) を表示するには、 **Force** パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="49002-162">Use the *Force* parameter to see system objects, such as the objects in the **sys** schema.</span></span>  
  
### <a name="custom-drives"></a><span data-ttu-id="49002-163">カスタム ドライブ</span><span class="sxs-lookup"><span data-stu-id="49002-163">Custom Drives</span></span>  
 <span data-ttu-id="49002-164">Windows PowerShell では、"PowerShell ドライブ" と呼ばれる仮想ドライブをユーザーが定義できます。</span><span class="sxs-lookup"><span data-stu-id="49002-164">Windows PowerShell lets users define virtual drives, which are referred to as PowerShell drives.</span></span> <span data-ttu-id="49002-165">これらのドライブには、パス ステートメントの開始ノードがマップされます。</span><span class="sxs-lookup"><span data-stu-id="49002-165">These map over the starting nodes of a path statement.</span></span> <span data-ttu-id="49002-166">これらは、通常、頻繁に入力されるパスを短縮するために使用します。</span><span class="sxs-lookup"><span data-stu-id="49002-166">They are typically used to shorten paths that are typed frequently.</span></span> <span data-ttu-id="49002-167">SQLSERVER: パスは長くなることがあり、長くなるとその分 Windows PowerShell ウィンドウ内の領域が使用され、多くの入力が必要になります。</span><span class="sxs-lookup"><span data-stu-id="49002-167">SQLSERVER: paths can get long, taking space in the Windows PowerShell window and requiring a lot of typing.</span></span> <span data-ttu-id="49002-168">特定のパス ノードで多くの作業を行う場合は、そのノードにマップされる Windows PowerShell のカスタム ドライブを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="49002-168">If you are going to do a lot of work at a particular path node, you can define a custom Windows PowerShell drive that maps to that node.</span></span>  
  
## <a name="use-powershell-cmdlet-aliases"></a><span data-ttu-id="49002-169">PowerShell コマンドレットの別名の使用</span><span class="sxs-lookup"><span data-stu-id="49002-169">Use PowerShell Cmdlet Aliases</span></span>  
 <span data-ttu-id="49002-170">**コマンドレットの別名の使用**</span><span class="sxs-lookup"><span data-stu-id="49002-170">**Use a cmdlet alias**</span></span>  
  
-   <span data-ttu-id="49002-171">完全なコマンドレット名を入力する代わりに、より短い別名、つまり使い慣れたコマンド プロンプト コマンドに割り当てられた名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="49002-171">Instead of typing a full cmdlet name, type a shorter alias, or one that maps to a familiar commend prompt command.</span></span>  
  
### <a name="alias-example-powershell"></a><span data-ttu-id="49002-172">別名の例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="49002-172">Alias Example (PowerShell)</span></span>  
 <span data-ttu-id="49002-173">たとえば、次に示す一連のコマンドレットまたは別名のいずれかを使用して、SQLSERVER:\SQL フォルダーに移動しフォルダーの子アイテムの一覧を要求することによって、使用できる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの一覧を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="49002-173">For example, you can use one of the following sets of cmdlets or aliases to retrieve a listing of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances available to you by navigating to the SQLSERVER:\SQL folder and requesting the list of child items for the folder:</span></span>  
  
```powershell
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a><span data-ttu-id="49002-174">Get-ChildItem の使用</span><span class="sxs-lookup"><span data-stu-id="49002-174">Use Get-ChildItem</span></span>  

### <a name="return-information-by-using-get-childitem"></a><span data-ttu-id="49002-175">Get-childitem を使用した情報の取得</span><span class="sxs-lookup"><span data-stu-id="49002-175">Return information by using Get-Childitem</span></span>
  
1.  <span data-ttu-id="49002-176">子の一覧を取得する対象のノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="49002-176">Navigate to the node for which you want a list of childrem</span></span>  
  
2.  <span data-ttu-id="49002-177">Get-childitem を実行して、一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="49002-177">Run Get-Childitem to get the list.</span></span>  
  
### <a name="get-childitem-example-powershell"></a><span data-ttu-id="49002-178">Get-ChildItem の例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="49002-178">Get-ChildItem Example (PowerShell)</span></span>  
 <span data-ttu-id="49002-179">これらの例は、SQL Server プロバイダー パス内の異なるノードについて、Get-Childitem で返される情報を示しています。</span><span class="sxs-lookup"><span data-stu-id="49002-179">These examples illustrate the information returned by Get-Childitem for different nodes in a SQL Server provider path.</span></span>  
  
```powershell
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a><span data-ttu-id="49002-180">カスタム ドライブの作成</span><span class="sxs-lookup"><span data-stu-id="49002-180">Create a Custom Drive</span></span>  

### <a name="create-and-use-a-custom-drive"></a><span data-ttu-id="49002-181">カスタム ドライブの作成と使用</span><span class="sxs-lookup"><span data-stu-id="49002-181">Create and use a custom drive</span></span>
  
1.  <span data-ttu-id="49002-182">`New-PSDrive` を使用して、カスタム ドライブを定義します。</span><span class="sxs-lookup"><span data-stu-id="49002-182">Use `New-PSDrive` to define a custom drive.</span></span> <span data-ttu-id="49002-183">`Root` パラメーターを使用して、カスタム ドライブ名で表されるパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="49002-183">Use the `Root` parameter to specify the path that is represented by the custom drive name.</span></span>  
  
2.  <span data-ttu-id="49002-184">`Set-Location` などのパス移動コマンドレットでカスタム ドライブ名を参照します。</span><span class="sxs-lookup"><span data-stu-id="49002-184">Reference the custom drive name in path navigation cmdlets such as `Set-Location`.</span></span>  
  
### <a name="custom-drive-example-powershell"></a><span data-ttu-id="49002-185">カスタム ドライブの例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="49002-185">Custom Drive Example (PowerShell)</span></span>  
 <span data-ttu-id="49002-186">この例では、配置された AdventureWorks2012 サンプル データベースのコピーのノードにマップする AWDB という名前の仮想ドライブを作成します。</span><span class="sxs-lookup"><span data-stu-id="49002-186">This example creates a virtual drive named AWDB that maps to the node for a deployed copy of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="49002-187">仮想ドライブを使用して、データベース内のテーブルに移動します。</span><span class="sxs-lookup"><span data-stu-id="49002-187">The virtual drive is then used to navigate to a table in the database.</span></span>  
  
```powershell
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a><span data-ttu-id="49002-188">参照</span><span class="sxs-lookup"><span data-stu-id="49002-188">See Also</span></span>  
 <span data-ttu-id="49002-189">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="49002-189">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="49002-190">[SQL Server PowerShell パスを操作する](work-with-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="49002-190">[Work With SQL Server PowerShell Paths](work-with-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="49002-191">[Urn を SQL Server プロバイダーのパスに変換する](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="49002-191">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="49002-192">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="49002-192">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
