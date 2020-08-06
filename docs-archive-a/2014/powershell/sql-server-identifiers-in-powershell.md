---
title: PowerShell での SQL Server 識別子 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c54fb352fb17c099bda78c80f00f91dbba428f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714446"
---
# <a name="sql-server-identifiers-in-powershell"></a><span data-ttu-id="e01f4-102">PowerShell での SQL Server 識別子</span><span class="sxs-lookup"><span data-stu-id="e01f4-102">SQL Server Identifiers in PowerShell</span></span>
  <span data-ttu-id="e01f4-103">Windows PowerShell 用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーは、Windows Powershell のパスに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell uses [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers in Windows PowerShell paths.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e01f4-104">識別子には、Windows PowerShell でパスとしてサポートされない文字が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e01f4-104">identifiers can contain characters that Windows PowerShell does not support in paths.</span></span> <span data-ttu-id="e01f4-105">Windows PowerShell パスでこの識別子を使用する場合は、これらの文字をエスケープするか、この文字に特殊なエンコードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e01f4-105">You must escape these characters or use special encoding for them when using the identifiers in Windows PowerShell paths.</span></span>  
  
## <a name="sql-server-identifiers-in-windows-powershell-paths"></a><span data-ttu-id="e01f4-106">Windows PowerShell パス内の SQL Server 識別子</span><span class="sxs-lookup"><span data-stu-id="e01f4-106">SQL Server Identifiers in Windows PowerShell Paths</span></span>  
 <span data-ttu-id="e01f4-107">Windows PowerShell プロバイダーは、Windows ファイル システムで使用されるようなパス構造を使用してデータ階層を公開します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-107">Windows PowerShell providers expose data hierarchies using a path structure similar to that used for the Windows file system.</span></span> <span data-ttu-id="e01f4-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトへのパスを実装します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-108">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements paths to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span> <span data-ttu-id="e01f4-109">[!INCLUDE[ssDE](../includes/ssde-md.md)]については、ドライブが SQLSERVER: に、最初のフォルダーが \SQL に設定され、データベース オブジェクトがコンテナーおよびアイテムとして参照されます。</span><span class="sxs-lookup"><span data-stu-id="e01f4-109">For the [!INCLUDE[ssDE](../includes/ssde-md.md)], the drive is set to SQLSERVER:, the first folder is set to \SQL, and the database objects are referenced as containers and items.</span></span> <span data-ttu-id="e01f4-110">これは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] の既定のインスタンスにある [!INCLUDE[ssDE](../includes/ssde-md.md)]データベースの Purchasing スキーマ内の Vendor テーブルへのパスです。</span><span class="sxs-lookup"><span data-stu-id="e01f4-110">This is the path to the Vendor table in the Purchasing schema of the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database in a default instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)]:</span></span>  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e01f4-111">識別子は、テーブル名や列名などの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの名前です。</span><span class="sxs-lookup"><span data-stu-id="e01f4-111">identifiers are the names of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects, such as table or column names.</span></span> <span data-ttu-id="e01f4-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別子には 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="e01f4-112">There are two types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers:</span></span>  
  
-   <span data-ttu-id="e01f4-113">標準識別子には、Windows PowerShell パスでもサポートされている一連の文字のみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e01f4-113">Regular identifiers are limited to a set of characters that are also supported in Windows PowerShell paths.</span></span> <span data-ttu-id="e01f4-114">これらの名前は、変更することなく Windows PowerShell パスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e01f4-114">These names can be used in Windows PowerShell paths without being changed.</span></span>  
  
-   <span data-ttu-id="e01f4-115">区切られた識別子には、Windows PowerShell パス名ではサポートされない文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e01f4-115">Delimited identifiers can use characters not supported in Windows PowerShell path names.</span></span> <span data-ttu-id="e01f4-116">区切られた識別子には、角かっこで囲まれた識別子 ([IdentifierName]) と二重引用符で囲まれた識別子 ("IdentifierName") があります。</span><span class="sxs-lookup"><span data-stu-id="e01f4-116">Delimited identifiers are called bracketed identifiers if they are enclosed in brackets ([IdentifierName]) and quoted identifiers if they are enclosed in double quotes ("IdentifierName").</span></span> <span data-ttu-id="e01f4-117">区切られた識別子に Windows PowerShell パスではサポートされない文字を使用する場合は、識別子をコンテナー名またはアイテム名として使用する前に、その文字をエンコードまたはエスケープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e01f4-117">If a delimited identifier uses characters not supported in Windows PowerShell paths, the characters must either be encoded or escaped before using the identifier as a container or item name.</span></span> <span data-ttu-id="e01f4-118">エンコードはすべての文字に有効です。</span><span class="sxs-lookup"><span data-stu-id="e01f4-118">Encoding works for all characters.</span></span> <span data-ttu-id="e01f4-119">コロン (:) などの一部の文字は、エスケープできません。</span><span class="sxs-lookup"><span data-stu-id="e01f4-119">Some characters, such as the colon character (:), cannot be escaped.</span></span>  
  
## <a name="sql-server-identifiers-in-cmdlets"></a><span data-ttu-id="e01f4-120">コマンドレットでの SQL Server 識別子</span><span class="sxs-lookup"><span data-stu-id="e01f4-120">SQL Server Identifiers in cmdlets</span></span>  
 <span data-ttu-id="e01f4-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コマンドレットには、識別子を入力として使用するパラメーターを持つものがあります。</span><span class="sxs-lookup"><span data-stu-id="e01f4-121">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets have a parameter that takes an identifier as input.</span></span> <span data-ttu-id="e01f4-122">このパラメーターの値は、通常、引用符で囲まれた文字列定数として指定されるか、文字列変数で指定されます。</span><span class="sxs-lookup"><span data-stu-id="e01f4-122">The parameter values are typically supplied as quoted string constants or in string variables.</span></span> <span data-ttu-id="e01f4-123">識別子を文字列定数または文字列変数で指定すると、Windows PowerShell でサポートされる一連の文字と競合することがありません。</span><span class="sxs-lookup"><span data-stu-id="e01f4-123">When identifiers are supplied as string constants or in variables, there is no conflict with the set of characters that are supported by Windows PowerShell.</span></span>  
  
## <a name="sql-server-identifier-tasks"></a><span data-ttu-id="e01f4-124">SQL Server 識別子のタスク</span><span class="sxs-lookup"><span data-stu-id="e01f4-124">SQL Server Identifier Tasks</span></span>  
  
|<span data-ttu-id="e01f4-125">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="e01f4-125">Task Description</span></span>|<span data-ttu-id="e01f4-126">トピック</span><span class="sxs-lookup"><span data-stu-id="e01f4-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e01f4-127">インスタンス名 (インスタンスが実行されているコンピューターの名前を含む) の指定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-127">Describes how to specify an instance name, including the name of the computer the instance is running on.</span></span>|[<span data-ttu-id="e01f4-128">SQL Server PowerShell プロバイダーでのインスタンスの指定</span><span class="sxs-lookup"><span data-stu-id="e01f4-128">Specify Instances in the SQL Server PowerShell Provider</span></span>](sql-server-powershell-provider.md)|  
|<span data-ttu-id="e01f4-129">Windows PowerShell のパスでサポートされていない区切られた識別子において、文字の 16 進エンコードを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-129">Describes how to specify the hexadecimal encoding for characters in delimited identifiers that are not supported in Windows PowerShell paths.</span></span> <span data-ttu-id="e01f4-130">また、16 進文字をデコードする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-130">Also describes how to decode the hexadecimal characters.</span></span>|[<span data-ttu-id="e01f4-131">SQL Server 識別子のエンコードとデコード</span><span class="sxs-lookup"><span data-stu-id="e01f4-131">Encode and Decode SQL Server Identifiers</span></span>](encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="e01f4-132">Windows PowerShell のパスでサポートされない文字にエスケープ文字を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e01f4-132">Describes how to use the Windows PowerShell escape character for characters not supported in PowerShell paths.</span></span>|[<span data-ttu-id="e01f4-133">SQL Server 識別子のエスケープ</span><span class="sxs-lookup"><span data-stu-id="e01f4-133">Escape SQL Server Identifiers</span></span>](escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a><span data-ttu-id="e01f4-134">参照</span><span class="sxs-lookup"><span data-stu-id="e01f4-134">See Also</span></span>  
 <span data-ttu-id="e01f4-135">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="e01f4-135">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="e01f4-136">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="e01f4-136">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="e01f4-137">データベース識別子</span><span class="sxs-lookup"><span data-stu-id="e01f4-137">Database Identifiers</span></span>](../relational-databases/databases/database-identifiers.md)  
  
  
