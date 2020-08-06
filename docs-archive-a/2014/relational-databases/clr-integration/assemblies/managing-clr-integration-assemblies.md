---
title: CLR 統合アセンブリの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: 191ccd73ca42ef4c26291e6de88f5f2b0cf565ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720024"
---
# <a name="managing-clr-integration-assemblies"></a><span data-ttu-id="3e110-102">CLR 統合アセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="3e110-102">Managing CLR Integration Assemblies</span></span>
  <span data-ttu-id="3e110-103">マネージド コードは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。</span><span class="sxs-lookup"><span data-stu-id="3e110-103">Managed code is compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="3e110-104">アセンブリは DLL ファイルまたは実行可能 (.exe) ファイルとしてパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="3e110-104">An assembly is packaged as a DLL or executable (.exe) file.</span></span> <span data-ttu-id="3e110-105">実行可能ファイルが単独で実行できるのに対し、DLL は既存のアプリケーションでホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e110-105">While an executable file can run on its own, a DLL must be hosted in an existing application.</span></span> <span data-ttu-id="3e110-106">マネージ DLL アセンブリは、に読み込んでホストすることができ [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3e110-106">Managed DLL assemblies can be loaded into and hosted by [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="3e110-107">CREATE ASSEMBLY ステートメントを使用して、データベースをプロセスに読み込み、使用する前に使用します。</span><span class="sxs-lookup"><span data-stu-id="3e110-107">database using the CREATE ASSEMBLY statement, before it can be loaded in the process and used.</span></span> <span data-ttu-id="3e110-108">アセンブリは、ALTER ASSEMBLY ステートメントを使用してより最近のバージョンから更新することも、DROP ASSEMBLY ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から削除することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3e110-108">Assemblies can also be updated from a more recent version using the ALTER ASSEMBLY statement, or removed from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] using the DROP ASSEMBLY statement.</span></span>  
  
 <span data-ttu-id="3e110-109">アセンブリ情報は、アセンブリがインストールされているデータベース内の `sys.assembly_files` テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3e110-109">Assembly information is stored in the `sys.assembly_files` table in the database where the assembly has been installed.</span></span> <span data-ttu-id="3e110-110">`sys.assembly_files` テーブルには、次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3e110-110">The `sys.assembly_files` table contains the following columns.</span></span>  
  
|<span data-ttu-id="3e110-111">列</span><span class="sxs-lookup"><span data-stu-id="3e110-111">Column</span></span>|<span data-ttu-id="3e110-112">説明</span><span class="sxs-lookup"><span data-stu-id="3e110-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3e110-113">assembly_id</span><span class="sxs-lookup"><span data-stu-id="3e110-113">assembly_id</span></span>|<span data-ttu-id="3e110-114">アセンブリに定義される ID。</span><span class="sxs-lookup"><span data-stu-id="3e110-114">The identifier defined for the assembly.</span></span> <span data-ttu-id="3e110-115">この番号は、同じアセンブリに関連するすべてのオブジェクトに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3e110-115">This number is assigned to all objects relating to the same assembly.</span></span>|  
|<span data-ttu-id="3e110-116">name</span><span class="sxs-lookup"><span data-stu-id="3e110-116">name</span></span>|<span data-ttu-id="3e110-117">オブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="3e110-117">The name of the object.</span></span>|  
|<span data-ttu-id="3e110-118">file_id</span><span class="sxs-lookup"><span data-stu-id="3e110-118">file_id</span></span>|<span data-ttu-id="3e110-119">各オブジェクトを識別する番号。最初のオブジェクトは、値 1 が割り当てられている所定の `assembly_id` に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="3e110-119">A number identifying each object, with the first object associated with a given `assembly_id` being given the value of 1.</span></span> <span data-ttu-id="3e110-120">複数のオブジェクトが同じ `assembly_id` に関連付けられている場合、その後に続く各 `file_id` 値は 1 ずつ増加します。</span><span class="sxs-lookup"><span data-stu-id="3e110-120">If multiple objects are associated with the same `assembly_id`, then each subsequent `file_id` value is incremented by 1.</span></span>|  
|<span data-ttu-id="3e110-121">コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3e110-121">content</span></span>|<span data-ttu-id="3e110-122">アセンブリまたはファイルの 16 進数表記。</span><span class="sxs-lookup"><span data-stu-id="3e110-122">The hexadecimal representation of the assembly or file.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="3e110-123">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3e110-123">In This Section</span></span>  
 [<span data-ttu-id="3e110-124">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="3e110-124">Creating an Assembly</span></span>](creating-an-assembly.md)  
 <span data-ttu-id="3e110-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における SAFE、EXTERNAL_ACCESS、および UNSAFE CLR アセンブリの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e110-125">Discusses creating SAFE, EXTERNAL_ACCESS, and UNSAFE CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="3e110-126">アセンブリの変更</span><span class="sxs-lookup"><span data-stu-id="3e110-126">Altering an Assembly</span></span>](altering-an-assembly.md)  
 <span data-ttu-id="3e110-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における CLR アセンブリの更新について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e110-127">Describes updating CLR assemblies in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="3e110-128">アセンブリの削除</span><span class="sxs-lookup"><span data-stu-id="3e110-128">Dropping an Assembly</span></span>](dropping-an-assembly.md)  
 <span data-ttu-id="3e110-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からの CLR アセンブリの削除について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e110-129">Discusses dropping CLR assemblies from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e110-130">参照</span><span class="sxs-lookup"><span data-stu-id="3e110-130">See Also</span></span>  
 <span data-ttu-id="3e110-131">[CLR 統合のセキュリティ](../security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="3e110-131">[CLR Integration Security](../security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="3e110-132">CLR 統合のコード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3e110-132">CLR Integration Code Access Security</span></span>](../security/clr-integration-code-access-security.md)  
  
  
