---
title: '[パッケージのロール] ダイアログボックスの UI リファレンス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 389b29ddee5674af7ecd106f4f82d61bbb3a0f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718555"
---
# <a name="package-roles-dialog-box-ui-reference"></a><span data-ttu-id="14954-102">[パッケージのロール] ダイアログ ボックスの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="14954-102">Package Roles Dialog Box UI Reference</span></span>
  <span data-ttu-id="14954-103">**の** [パッケージのロール] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用すると、パッケージに対する読み取りアクセス権のあるデータベースレベル ロールおよびパッケージに対する書き込みアクセス権のあるデータベースレベル ロールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="14954-103">Use the **Package Roles** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to specify the database-level roles that have read access to the package and the database-level roles that have write access to the package.</span></span> <span data-ttu-id="14954-104">データベースレベル ロールは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** データベースに格納されたパッケージにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="14954-104">Database-level roles apply only to packages that are stored in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** database.</span></span>  
  
 <span data-ttu-id="14954-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] データベースレベルのロールとそのアクセス許可の詳細については、「[Integration Services のロール (SSIS サービス)](security/integration-services-roles-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14954-105">To learn more about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] database-level roles and their permissions, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>  
  
 <span data-ttu-id="14954-106">ダイアログ ボックスに一覧表示されたロールは、 **msdb** システム データベースの現在のデータベース ロールです。</span><span class="sxs-lookup"><span data-stu-id="14954-106">The roles listed in the dialog box are the current database roles of the **msdb** system database.</span></span> <span data-ttu-id="14954-107">ロールが選択されていない場合は、既定の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ロールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="14954-107">If no roles are selected, the default [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] roles apply.</span></span> <span data-ttu-id="14954-108">リーダー ロールには、既定では、 **db_ssisadmin**および **db_ssisoperator**と、パッケージを作成したユーザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="14954-108">By default, the reader role includes **db_ssisadmin**, **db_ssisoperator**, and the user who created the package.</span></span> <span data-ttu-id="14954-109">ユーザーがこれらのロールのいずれかのメンバー、またはパッケージを作成したユーザーである場合は、パッケージの列挙、表示、エクスポート、および実行が可能です。</span><span class="sxs-lookup"><span data-stu-id="14954-109">A user who is a member of one of these roles or created the packages can enumerate, view, export, and run packages.</span></span> <span data-ttu-id="14954-110">ライター ロールには、既定では、 **db_ssisadmin** と、パッケージを作成したユーザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="14954-110">By default, the writer role includes **db_ssisadmin** and the user who created the package.</span></span> <span data-ttu-id="14954-111">ユーザーがこのロールのメンバー、またはパッケージを作成したユーザーである場合は、パッケージのインポート、削除、変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="14954-111">A user who is a member of this role and the user who created the packages can import, delete, and change packages.</span></span>  
  
 <span data-ttu-id="14954-112">**sysssispackages** テーブルの **ownersid** 列には、パッケージを作成したユーザーの一意なセキュリティ識別子が表示されます。</span><span class="sxs-lookup"><span data-stu-id="14954-112">The **ownersid** column in the **sysssispackages** table lists the unique security identifier of the user who created the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="14954-113">Options</span><span class="sxs-lookup"><span data-stu-id="14954-113">Options</span></span>  
 <span data-ttu-id="14954-114">**パッケージ名**</span><span class="sxs-lookup"><span data-stu-id="14954-114">**Package Name**</span></span>  
 <span data-ttu-id="14954-115">パッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="14954-115">Specify the name of the package.</span></span>  
  
 <span data-ttu-id="14954-116">**閲覧者ロール**</span><span class="sxs-lookup"><span data-stu-id="14954-116">**Reader Role**</span></span>  
 <span data-ttu-id="14954-117">ロールを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="14954-117">Select a role in the list.</span></span>  
  
 <span data-ttu-id="14954-118">**[ライター ロール]**</span><span class="sxs-lookup"><span data-stu-id="14954-118">**Writer Role**</span></span>  
 <span data-ttu-id="14954-119">ロールを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="14954-119">Select a role in the list</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14954-120">参照</span><span class="sxs-lookup"><span data-stu-id="14954-120">See Also</span></span>  
 <span data-ttu-id="14954-121">[データベース レベルのロール](../relational-databases/security/authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="14954-121">[Database-Level Roles](../relational-databases/security/authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="14954-122">セキュリティの概要 &#40;Integration Services&#41;</span><span class="sxs-lookup"><span data-stu-id="14954-122">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
