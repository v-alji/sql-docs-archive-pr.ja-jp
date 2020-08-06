---
title: Transact-SQL での OLE オートメーション オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f36846565bb60fbf875e9babdabbb6d1667f5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646128"
---
# <a name="ole-automation-objects-in-transact-sql"></a><span data-ttu-id="05845-102">Transact-SQL での OLE オートメーション オブジェクト</span><span class="sxs-lookup"><span data-stu-id="05845-102">OLE Automation Objects in Transact-SQL</span></span>
  [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="05845-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ、ストアド プロシージャ、およびトリガーの中で OLE オートメーション オブジェクトを参照できるいくつかのシステム ストアド プロシージャが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="05845-103">includes several system stored procedures that allow OLE Automation objects to be referenced in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, stored procedures, and triggers.</span></span> <span data-ttu-id="05845-104">これらのシステム ストアド プロシージャは拡張ストアド プロシージャとして動作します。また、これらのストアド プロシージャから実行される OLE オートメーション オブジェクトは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] アドレス空間の中で拡張ストアド プロシージャと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="05845-104">These system stored procedures run as extended stored procedures, and the OLE Automation objects that are executed through the stored procedures run in the address space of an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in the same way that an extended stored procedure runs.</span></span>  
  
 <span data-ttu-id="05845-105">OLE オートメーション ストアド プロシージャでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチから SQL DMO オブジェクトやカスタム OLE オートメーション オブジェクト ( **IDispatch** インターフェイスを公開しているオブジェクトなど) を参照できます。</span><span class="sxs-lookup"><span data-stu-id="05845-105">The OLE Automation stored procedures enable [!INCLUDE[tsql](../../includes/tsql-md.md)] batches to reference SQL-DMO objects and custom OLE Automation objects, such as objects that expose the **IDispatch** interface.</span></span> <span data-ttu-id="05845-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] を使用して作成するカスタム インプロセス OLE サーバーには、**Class_Initialize** サブルーチンと **Class_Terminate** サブルーチン用に (**On Error GoTo** ステートメントで指定された) エラー ハンドラーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05845-106">A custom in-process OLE server that is created by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] must have an error handler (specified with the **On Error GoTo** statement) for the **Class_Initialize** and **Class_Terminate** subroutines.</span></span> <span data-ttu-id="05845-107">**Class_Initialize** サブルーチンと **Class_Terminate** サブルーチンで処理されないエラーが発生すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスでのアクセス違反など、予期しないエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="05845-107">Unhandled errors in the **Class_Initialize** and **Class_Terminate** subroutines can cause unpredictable errors, such as an access violation in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="05845-108">また、その他のサブルーチン用のエラー ハンドラーも用意しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="05845-108">Error handlers for other subroutines are also recommended.</span></span>  
  
 <span data-ttu-id="05845-109">[!INCLUDE[tsql](../../includes/tsql-md.md)] で OLE オートメーション オブジェクトを使用する場合は、まず、**sp_OACreate[!INCLUDE[ssDE](../../includes/ssde-md.md)] システム ストアド プロシージャを呼び出して、** のインスタンスのアドレス空間にそのオブジェクトのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="05845-109">The first step when using an OLE Automation object in [!INCLUDE[tsql](../../includes/tsql-md.md)] is to call the **sp_OACreate** system stored procedure to create an instance of the object in the address space of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="05845-110">オブジェクトのインスタンスを作成した後、次のストアド プロシージャを呼び出してオブジェクトのプロパティ、メソッド、およびエラー情報を処理します。</span><span class="sxs-lookup"><span data-stu-id="05845-110">After an instance of the object has been created, call the following stored procedures to work with the properties, methods, and error information related to the object:</span></span>  
  
-   <span data-ttu-id="05845-111">**sp_OAGetProperty** はプロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="05845-111">**sp_OAGetProperty** obtains the value of a property.</span></span>  
  
-   <span data-ttu-id="05845-112">**sp_OASetProperty** はプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="05845-112">**sp_OASetProperty** sets the value of a property.</span></span>  
  
-   <span data-ttu-id="05845-113">**sp_OAMethod** はメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="05845-113">**sp_OAMethod** calls a method.</span></span>  
  
-   <span data-ttu-id="05845-114">**sp_OAGetErrorInfo** は最新のエラー情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="05845-114">**sp_OAGetErrorInfo** obtains the most recent error information.</span></span>  
  
 <span data-ttu-id="05845-115">オブジェクトが必要なくなったら、 **sp_OADestroy** を呼び出し、 **sp_OACreate**で作成したオブジェクトのインスタンスの割り当てを解除します。</span><span class="sxs-lookup"><span data-stu-id="05845-115">When there is no more need for the object, call **sp_OADestroy** to deallocate the instance of the object created by using **sp_OACreate**.</span></span>  
  
 <span data-ttu-id="05845-116">OLE オートメーション オブジェクトは、プロパティ値とメソッドを使用してデータを返します。</span><span class="sxs-lookup"><span data-stu-id="05845-116">OLE Automation objects return data through property values and methods.</span></span> <span data-ttu-id="05845-117">**sp_OAGetProperty** と **sp_OAMethod** は、これらのデータ値を結果セットの形で返します。</span><span class="sxs-lookup"><span data-stu-id="05845-117">**sp_OAGetProperty** and **sp_OAMethod** return these data values in the form of a result set.</span></span>  
  
 <span data-ttu-id="05845-118">OLE オートメーション オブジェクトのスコープはバッチです。</span><span class="sxs-lookup"><span data-stu-id="05845-118">The scope of an OLE Automation object is a batch.</span></span> <span data-ttu-id="05845-119">そのオブジェクトへのすべての参照は、単一のバッチ、ストアド プロシージャ、またはトリガー内に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="05845-119">All references to the object must be contained in a single batch, stored procedure, or trigger.</span></span>  
  
 <span data-ttu-id="05845-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の OLE オートメーション オブジェクトからオブジェクトを参照する場合、参照するオブジェクトに含まれる他のオブジェクトも参照できます。</span><span class="sxs-lookup"><span data-stu-id="05845-120">When it references objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE Automation objects support traversing the referenced object to other objects that it contains.</span></span> <span data-ttu-id="05845-121">たとえば、SQL-DMO の **SQLServer** オブジェクトを使用すると、参照先のサーバーに含まれているデータベースとテーブルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="05845-121">For example, when using the SQL-DMO **SQLServer** object, references can be made to databases and tables contained on that server.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="05845-122">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="05845-122">Related Content</span></span>  
 [<span data-ttu-id="05845-123">オブジェクト階層構文 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-123">Object Hierarchy Syntax &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql)  
  
 [<span data-ttu-id="05845-124">セキュリティ構成</span><span class="sxs-lookup"><span data-stu-id="05845-124">Surface Area Configuration</span></span>](../security/surface-area-configuration.md)  
  
 [<span data-ttu-id="05845-125">Ole Automation Procedures サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="05845-125">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [<span data-ttu-id="05845-126">sp_OACreate &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-126">sp_OACreate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oacreate-transact-sql)  
  
 [<span data-ttu-id="05845-127">sp_OAGetProperty &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-127">sp_OAGetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql)  
  
 [<span data-ttu-id="05845-128">sp_OASetProperty &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-128">sp_OASetProperty &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql)  
  
 [<span data-ttu-id="05845-129">sp_OAMethod &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-129">sp_OAMethod &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oamethod-transact-sql)  
  
 [<span data-ttu-id="05845-130">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-130">sp_OAGetErrorInfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
 [<span data-ttu-id="05845-131">sp_OADestroy &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05845-131">sp_OADestroy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-oadestroy-transact-sql)  
  
  
