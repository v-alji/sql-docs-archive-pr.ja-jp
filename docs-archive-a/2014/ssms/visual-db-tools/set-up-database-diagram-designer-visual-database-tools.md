---
title: データベース ダイアグラム デザイナーの設定 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d59fa2ed197a410de6b68e388e76d2bf21c334d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719305"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a><span data-ttu-id="2ac53-102">データベース ダイアグラム デザイナーの設定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2ac53-102">Set Up Database Diagram Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="2ac53-103">データベース ダイアグラム デザイナーを使用するには、 **db_owner** ロールのメンバーによって、ダイアグラムへのアクセスを制御するようにあらかじめ設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ac53-103">To use Database Diagram Designer, it must first be set up by a member of the **db_owner** role to control access to diagrams.</span></span>  
  
### <a name="to-set-up-database-diagramming"></a><span data-ttu-id="2ac53-104">データベース ダイアグラムを設定するには</span><span class="sxs-lookup"><span data-stu-id="2ac53-104">To set up database diagramming</span></span>  
  
1.  <span data-ttu-id="2ac53-105">オブジェクト エクスプローラーから、データベース ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2ac53-105">From Object Explorer, expand a database node.</span></span>  
  
2.  <span data-ttu-id="2ac53-106">データベース接続のデータベース ダイアグラム ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2ac53-106">Expand the Database Diagrams node under the database connection.</span></span>  
  
3.  <span data-ttu-id="2ac53-107">データベースのダイアグラム化を設定するかどうかをたずねるメッセージが表示されたら、 **[はい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ac53-107">Select **Yes** when prompted if you want to set up database diagramming.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2ac53-108">これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにデータベース ダイアグラム テーブル、システム ストアド プロシージャ、およびシステム関数が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2ac53-108">This will create the database diagram table, system stored procedures, and a system function on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="2ac53-109">Visual Studio では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに次のオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2ac53-109">Visual Studio will create the following objects on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="2ac53-110">sysdiagrams テーブル</span><span class="sxs-lookup"><span data-stu-id="2ac53-110">sysdiagrams table</span></span>  
  
    2.  <span data-ttu-id="2ac53-111">sp_alterdiagram ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-111">sp_alterdiagram stored procedure</span></span>  
  
    3.  <span data-ttu-id="2ac53-112">sp_creatediagram ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-112">sp_creatediagram stored procedure</span></span>  
  
    4.  <span data-ttu-id="2ac53-113">sp_dropdiagram ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-113">sp_dropdiagram stored procedure</span></span>  
  
    5.  <span data-ttu-id="2ac53-114">sp_renamediagram ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-114">sp_renamediagram stored procedure</span></span>  
  
    6.  <span data-ttu-id="2ac53-115">fn_diagramobjects 関数</span><span class="sxs-lookup"><span data-stu-id="2ac53-115">fn_diagramobjects function</span></span>  
  
    7.  <span data-ttu-id="2ac53-116">sp_helpdiagrams ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-116">sp_helpdiagrams stored procedure</span></span>  
  
    8.  <span data-ttu-id="2ac53-117">sp_helpdiagramsdefinition ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-117">sp_helpdiagramsdefinition stored procedure</span></span>  
  
    9. <span data-ttu-id="2ac53-118">sp_upgraddiagrams ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2ac53-118">sp_upgraddiagrams stored procedure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac53-119">参照</span><span class="sxs-lookup"><span data-stu-id="2ac53-119">See Also</span></span>  
 <span data-ttu-id="2ac53-120">[Visual Database Tools &#40;データベースダイアグラムの所有権について&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2ac53-120">[Understand Database Diagram Ownership &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="2ac53-121">[以前のエディションのデータベースダイアグラムをアップグレードする &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2ac53-121">[Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2ac53-122">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ac53-122">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
