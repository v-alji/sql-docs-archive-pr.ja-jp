---
title: データベース エンジン PowerShell での認証の管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 018a2698a43148af971622f54c8418bf23c2c781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713226"
---
# <a name="manage-authentication-in-database-engine-powershell"></a><span data-ttu-id="479d1-102">データベース エンジン PowerShell での認証の管理</span><span class="sxs-lookup"><span data-stu-id="479d1-102">Manage Authentication in Database Engine PowerShell</span></span>
  <span data-ttu-id="479d1-103">既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell コンポーネントは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]インスタンスへの接続に Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="479d1-103">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components use Windows Authentication when connecting to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="479d1-104">SQL Server 認証を使用するには、PowerShell 仮想ドライブを定義するか、`-Username` の `-Password` および `Invoke-Sqlcmd` パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="479d1-104">You can use SQL Server Authentication by either defining a PowerShell virtual drive, or by specifying the `-Username` and `-Password` parameters for `Invoke-Sqlcmd`.</span></span>  
  
1.  <span data-ttu-id="479d1-105">**作業を開始する準備:** [アクセス許可](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="479d1-105">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="479d1-106">**認証を設定する方法:**  [仮想ドライブ](#SQLAuthVirtDrv)、 [–Password](#SQLAuthInvSqlCmd)</span><span class="sxs-lookup"><span data-stu-id="479d1-106">**To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="479d1-107">Permissions</span><span class="sxs-lookup"><span data-stu-id="479d1-107">Permissions</span></span>  
 <span data-ttu-id="479d1-108">[!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスで実行できるすべての操作は、そのインスタンスへの接続に使用された認証資格情報に付与されている権限によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="479d1-108">All actions you can perform in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] are controlled by the permissions granted to the authentication credentials used to connect to the instance.</span></span> <span data-ttu-id="479d1-109">既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーとコマンドレットは、それが実行されている Windows アカウントを使用して、 [!INCLUDE[ssDE](../includes/ssde-md.md)]への Windows 認証接続を行います。</span><span class="sxs-lookup"><span data-stu-id="479d1-109">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider and cmdlets use the Windows account under which it is running to make a Windows Authentication connection to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="479d1-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証接続を行うには、SQL Server 認証のログイン ID およびパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="479d1-110">To make a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication connection you must supply a SQL Server Authentication login ID and password.</span></span> <span data-ttu-id="479d1-111">プロバイダーを使用する場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログイン資格情報を仮想ドライブに関連付けてから、ディレクトリの変更コマンド () を使用して `cd` そのドライブに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="479d1-111">When using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider, you must associate the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login credentials with a virtual drive, and then use the change directory command (`cd`) to connect to that drive.</span></span> <span data-ttu-id="479d1-112">Windows PowerShell では、セキュリティ資格情報は仮想ドライブにのみ関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="479d1-112">In Windows PowerShell, security credentials can only be associated with virtual drives.</span></span>  
  
##  <a name="sql-server-authentication-using-a-virtual-drive"></a><a name="SQLAuthVirtDrv"></a><span data-ttu-id="479d1-113">仮想ドライブを使用した認証の SQL Server</span><span class="sxs-lookup"><span data-stu-id="479d1-113">SQL Server Authentication Using a Virtual Drive</span></span>  
 <span data-ttu-id="479d1-114">**SQL Server 認証ログインに関連付けられた仮想ドライブを作成するには**</span><span class="sxs-lookup"><span data-stu-id="479d1-114">**To create a virtual drive associated with a SQL Server Authentication login**</span></span>  
  
1.  <span data-ttu-id="479d1-115">次のような関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="479d1-115">Create a function that:</span></span>  
  
    1.  <span data-ttu-id="479d1-116">仮想ドライブに与える名前、ログイン ID、および仮想ドライブに関連付けるプロバイダー パスのためのパラメーターを持っている。</span><span class="sxs-lookup"><span data-stu-id="479d1-116">Has parameters for the name to give the virtual drive, the login ID, and the provider path to associate with the virtual drive.</span></span>  
  
    2.  <span data-ttu-id="479d1-117">`read-host` を使用して、ユーザーにパスワードの入力を求める。</span><span class="sxs-lookup"><span data-stu-id="479d1-117">Uses `read-host` to prompt the user for the password.</span></span>  
  
    3.  <span data-ttu-id="479d1-118">`new-object` を使用して、資格情報オブジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="479d1-118">Uses `new-object` to create a credentials object.</span></span>  
  
    4.  <span data-ttu-id="479d1-119">`new-psdrive` を使用して、指定された資格情報で仮想ドライブを作成する。</span><span class="sxs-lookup"><span data-stu-id="479d1-119">Uses `new-psdrive` to create a virtual drive with the supplied credentials.</span></span>  
  
2.  <span data-ttu-id="479d1-120">関数を呼び出して、指定された資格情報で仮想ドライブを作成します。</span><span class="sxs-lookup"><span data-stu-id="479d1-120">Invoke the function to create a virtual drive with the supplied credentials.</span></span>  
  
### <a name="example-virtual-drive"></a><span data-ttu-id="479d1-121">例 (仮想ドライブ)</span><span class="sxs-lookup"><span data-stu-id="479d1-121">Example (Virtual Drive)</span></span>  
 <span data-ttu-id="479d1-122">次の例は、指定された **認証ログインおよびインスタンスに関連付けられる仮想ドライブを作成するための、** sqldrive [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] という名前の関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="479d1-122">This example creates a function named **sqldrive** that you can use to create a virtual drive that is associated with the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login and instance.</span></span>  
  
 <span data-ttu-id="479d1-123">**sqldrive** 関数は、ユーザーにログインのパスワードの入力を求め、入力されるパスワードをマスクします。</span><span class="sxs-lookup"><span data-stu-id="479d1-123">The **sqldrive** function prompts you to enter the password for your login, masking the password as you type it in.</span></span> <span data-ttu-id="479d1-124">次に、ディレクトリの変更コマンド () を使用して `cd` 仮想ドライブ名を使用してパスに接続するたびに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ドライブの作成時に指定した認証ログイン資格情報を使用してすべての操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="479d1-124">Then, whenever you use the change directory command (`cd`) to connect to a path by using the virtual drive name, all operations are performed by using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login credentials that you supplied when you created the drive.</span></span>  
  
```powershell
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = Read-Host -AsSecureString -Prompt "Password"  
    $cred = New-Object System.Management.Automation.PSCredential -argumentlist $login, $pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="sql-server-authentication-using-invoke-sqlcmd"></a><a name="SQLAuthInvSqlCmd"></a><span data-ttu-id="479d1-125">Invoke を使用して認証を SQL Server する-Sqlcmd</span><span class="sxs-lookup"><span data-stu-id="479d1-125">SQL Server Authentication Using Invoke-Sqlcmd</span></span>  
 <span data-ttu-id="479d1-126">**SQL Server 認証で Invoke-Sqlcmd を使用するには**</span><span class="sxs-lookup"><span data-stu-id="479d1-126">**To use Invoke-Sqlcmd with SQL Server Authentication**</span></span>  
  
1.  <span data-ttu-id="479d1-127">`-Username` パラメーターでログイン ID を指定し、`-Password` パラメーターで関連付けられているパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="479d1-127">Use the `-Username` parameter to specify a login ID, and the `-Password` parameter to specify the associated password.</span></span>  
  
### <a name="example-invoke-sqlcmd"></a><span data-ttu-id="479d1-128">例 (Invoke-Sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="479d1-128">Example (Invoke-Sqlcmd)</span></span>  
 <span data-ttu-id="479d1-129">この例では、read-host コマンドレットを使用してユーザーにパスワードの入力を求め、SQL Server 認証を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="479d1-129">This example uses the read-host cmdlet to prompt the user for a password, and then connects using SQL Server Authentication.</span></span>  
  
```powershell
## Prompt the user for their password.  
$pwd = Read-Host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a><span data-ttu-id="479d1-130">参照</span><span class="sxs-lookup"><span data-stu-id="479d1-130">See Also</span></span>  
 <span data-ttu-id="479d1-131">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="479d1-131">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 <span data-ttu-id="479d1-132">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="479d1-132">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="479d1-133">Invoke-Sqlcmd コマンドレット</span><span class="sxs-lookup"><span data-stu-id="479d1-133">Invoke-Sqlcmd cmdlet</span></span>](../database-engine/invoke-sqlcmd-cmdlet.md)  
