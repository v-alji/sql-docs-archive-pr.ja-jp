---
title: SQL Server PowerShell プロバイダーでのインスタンスの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc04bacc1ff36b0b5ce526a377fcdb750ad134a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640105"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a><span data-ttu-id="3cfdd-102">SQL Server PowerShell プロバイダーでのインスタンスの指定</span><span class="sxs-lookup"><span data-stu-id="3cfdd-102">Specify Instances in the SQL Server PowerShell Provider</span></span>
  <span data-ttu-id="3cfdd-103">SQL Server PowerShell プロバイダーに指定するパスでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスと、それが実行されているコンピューターを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-103">The paths specified for the SQL Server PowerShell provider must identify the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] and the computer it is running on.</span></span> <span data-ttu-id="3cfdd-104">コンピューターおよびインスタンスを指定する構文は、SQL Server 識別子と Windows PowerShell パスの両方の規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-104">The syntax for specifying the computer and the instance must comply with both the rules for SQL Server identifiers and Windows PowerShell paths.</span></span>  
  
1.  <span data-ttu-id="3cfdd-105">**作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="3cfdd-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="3cfdd-106">**インスタンスの指定方法:**  [使用例](#Examples)</span><span class="sxs-lookup"><span data-stu-id="3cfdd-106">**To specify an instance:**  [Examples](#Examples)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="3cfdd-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="3cfdd-107">Before You Begin</span></span>  
 <span data-ttu-id="3cfdd-108">SQL Server プロバイダーのパスで SQLSERVER:\SQL に続く最初のノードは、たとえば次のような、 [!INCLUDE[ssDE](../includes/ssde-md.md)]のインスタンスが実行されているコンピューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-108">The first node following the SQLSERVER:\SQL in a SQL Server provider path is the name of the computer that is running the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 <span data-ttu-id="3cfdd-109">[!INCLUDE[ssDE](../includes/ssde-md.md)]のインスタンスと同じコンピューター上で Windows PowerShell を実行している場合は、コンピューター名の代わりに localhost または (local) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-109">If you are running Windows PowerShell on the same computer as the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], you can use either localhost or (local) instead of the name of the computer.</span></span> <span data-ttu-id="3cfdd-110">localhost または (local) が使用されたスクリプトは、異なるコンピューター名を反映するための変更を加えることなく、すべてのコンピューター上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-110">Scripts that use localhost or (local) can be run on any computer without having to be changed to reflect the different computer names.</span></span>  
  
 <span data-ttu-id="3cfdd-111">[!INCLUDE[ssDE](../includes/ssde-md.md)] の実行可能プログラムの複数のインスタンスを、同じコンピューターで実行できます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-111">You can run multiple instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] executable program on the same computer.</span></span> <span data-ttu-id="3cfdd-112">SQL Server プロバイダーのパスでコンピューター名に続くノードは、たとえば次のように、インスタンスを識別します。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-112">The node following the computer name in a SQL Server provider path identifies the instance; for example:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 <span data-ttu-id="3cfdd-113">各コンピューターでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]の既定のインスタンスを 1 つだけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-113">Each computer can have one default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="3cfdd-114">既定のインスタンスには、そのインストール時に名前を指定しません。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-114">You do not specify a name for the default instance when you install it.</span></span> <span data-ttu-id="3cfdd-115">接続文字列にコンピューター名のみを指定すると、そのコンピューターの既定のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-115">If you specify only a computer name in a connection string, you are connected to the default instance on that computer.</span></span> <span data-ttu-id="3cfdd-116">コンピューター上のその他すべてのインスタンスは、名前付きインスタンスにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-116">All other instances on the computer must be named instances.</span></span> <span data-ttu-id="3cfdd-117">インスタンス名はセットアップ時に指定します。接続文字列には、コンピューター名とインスタンス名の両方を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-117">You specify the instance name during setup, and connection strings must specify both the computer name and the instance name.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="3cfdd-118">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="3cfdd-118">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3cfdd-119">PowerShell スクリプトでは、ピリオド (.) を使用してローカル コンピューターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-119">You cannot use a period (.) to specify the local computer in PowerShell scripts.</span></span> <span data-ttu-id="3cfdd-120">PowerShell ではピリオドはコマンドとして解釈されるため、ピリオドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-120">The period is not supported because the period is interpreted as a command by PowerShell.</span></span>  
  
 <span data-ttu-id="3cfdd-121">通常、(local) に使用されているかっこ文字は、Windows PowerShell でコマンドとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-121">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="3cfdd-122">パス内で使用するには、エンコードするかエスケープする必要があります。または、パスを二重引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-122">You must either encode them or escape them for use in a path, or enclose the path in double-quotation marks.</span></span> <span data-ttu-id="3cfdd-123">詳細については、「SQL Server 識別子のエンコードとデコード」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-123">For more information, see Encode and Decode SQL Server Identifiers.</span></span>  
  
 <span data-ttu-id="3cfdd-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーでは、常にインスタンス名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-124">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider requires that you always specify an instance name.</span></span> <span data-ttu-id="3cfdd-125">既定のインスタンスには、DEFAULT というインスタンス名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-125">For default instances, you must specify an instance name of DEFAULT.</span></span>  
  
##  <a name="examples-computer-and-instance-names"></a><a name="Examples"></a><span data-ttu-id="3cfdd-126">例コンピューター名とインスタンス名</span><span class="sxs-lookup"><span data-stu-id="3cfdd-126">Examples; Computer and Instance Names</span></span>  
 <span data-ttu-id="3cfdd-127">この例では、次のように、localhost および DEFAULT を使用してローカル コンピューター上の既定のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-127">This example uses localhost and DEFAULT to specify the default instance on the local computer:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 <span data-ttu-id="3cfdd-128">通常、(local) に使用されているかっこ文字は、Windows PowerShell でコマンドとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-128">The parenthesis characters in (local) are normally treated as commands by Windows PowerShell.</span></span> <span data-ttu-id="3cfdd-129">次のいずれかの作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-129">You must either:</span></span>  
  
-   <span data-ttu-id="3cfdd-130">パス文字列を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-130">Enclose the path string in quotes:</span></span>  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   <span data-ttu-id="3cfdd-131">バック ティック文字 (') を使用して、かっこをエスケープします。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-131">Escape the parenthesis using the back tick character (\`):</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   <span data-ttu-id="3cfdd-132">16 進数表記を使用して、かっこをエンコードします。</span><span class="sxs-lookup"><span data-stu-id="3cfdd-132">Encode the parenthesis using their hexadecimal representation:</span></span>  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3cfdd-133">参照</span><span class="sxs-lookup"><span data-stu-id="3cfdd-133">See Also</span></span>  
 <span data-ttu-id="3cfdd-134">[PowerShell での SQL Server 識別子](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="3cfdd-134">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="3cfdd-135">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="3cfdd-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="3cfdd-136">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="3cfdd-136">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
