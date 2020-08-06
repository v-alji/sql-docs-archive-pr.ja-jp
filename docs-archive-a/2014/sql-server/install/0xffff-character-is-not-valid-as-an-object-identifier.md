---
title: 0xFFFF 文字はオブジェクト識別子として有効ではありません |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640512"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a><span data-ttu-id="1332c-102">0xFFFF 文字はオブジェクト識別子としては無効である</span><span class="sxs-lookup"><span data-stu-id="1332c-102">0xFFFF character is not valid as an object identifier</span></span>
  <span data-ttu-id="1332c-103">アップグレード アドバイザーによって、オブジェクト識別子に 0xFFFF 文字が検出されました。</span><span class="sxs-lookup"><span data-stu-id="1332c-103">Upgrade Advisor has detected the 0xFFFF character in an object identifier.</span></span> <span data-ttu-id="1332c-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、データベース、テーブル、列などのオブジェクトの識別子にこの文字が含まれていると、データベース互換性モードが 90 以上に設定されている場合にオブジェクトを参照したりオブジェクトの名前を変更することができません。</span><span class="sxs-lookup"><span data-stu-id="1332c-104">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, objects such as databases, tables, and columns that contain this character in their identifiers cannot be referenced or renamed when the database compatibility mode is set to 90 or later.</span></span> <span data-ttu-id="1332c-105">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] にアップグレードすると、ユーザー データベースでは互換性モードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="1332c-105">When you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], user databases maintain their compatibility mode.</span></span> <span data-ttu-id="1332c-106">データベース互換性モードを 90 以上に変更する前に、0xFFFF 文字を含むオブジェクトの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="1332c-106">Before you change the database compatibility mode to 90 or later, rename the object that contains the 0xFFFF character.</span></span>  
  
 <span data-ttu-id="1332c-107">識別子の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「識別子」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1332c-107">For more information about identifiers, see "Identifiers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="1332c-108">データベース互換性モードの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1332c-108">For more information about database compatibility modes, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="1332c-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1332c-109">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1332c-110">参照</span><span class="sxs-lookup"><span data-stu-id="1332c-110">See Also</span></span>  
 <span data-ttu-id="1332c-111">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="1332c-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="1332c-112">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="1332c-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
