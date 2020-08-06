---
title: filestream access level サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dfa43b8e6e1762e87dd9c2abbdf7a583963e196e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645209"
---
# <a name="filestream-access-level-server-configuration-option"></a><span data-ttu-id="b6798-102">filestream access level サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="b6798-102">filestream access level Server Configuration Option</span></span>
  <span data-ttu-id="b6798-103">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対する FILESTREAM のアクセス レベルを変更するには、filestream_access_level オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6798-103">Use the filestream_access_level option to change the FILESTREAM access level for this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6798-104">このオプションを有効にする前に、FILESTREAM の Windows 管理者設定を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6798-104">Before this option has any effect, the Windows administration settings for FILESTREAM must be enabled.</span></span> <span data-ttu-id="b6798-105">これらの設定は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に有効にできます。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b6798-105">You can enable these settings when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
|<span data-ttu-id="b6798-106">値</span><span class="sxs-lookup"><span data-stu-id="b6798-106">Value</span></span>|<span data-ttu-id="b6798-107">定義</span><span class="sxs-lookup"><span data-stu-id="b6798-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="b6798-108">0</span><span class="sxs-lookup"><span data-stu-id="b6798-108">0</span></span>|<span data-ttu-id="b6798-109">このインスタンスに対する FILESTREAM サポートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="b6798-109">Disables FILESTREAM support for this instance.</span></span>|  
|<span data-ttu-id="b6798-110">1</span><span class="sxs-lookup"><span data-stu-id="b6798-110">1</span></span>|<span data-ttu-id="b6798-111">[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b6798-111">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span>|  
|<span data-ttu-id="b6798-112">2</span><span class="sxs-lookup"><span data-stu-id="b6798-112">2</span></span>|<span data-ttu-id="b6798-113">[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスおよび Win32 ストリーム アクセスに対して FILESTREAM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b6798-113">Enables FILESTREAM for [!INCLUDE[tsql](../../includes/tsql-md.md)] and Win32 streaming access.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6798-114">参照</span><span class="sxs-lookup"><span data-stu-id="b6798-114">See Also</span></span>  
 <span data-ttu-id="b6798-115">[データベース エンジンの構成 - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="b6798-115">[Database Engine Configuration - Filestream](../../sql-server/install/database-engine-configuration-filestream.md) </span></span>  
 [<span data-ttu-id="b6798-116">FILESTREAM の有効化と構成</span><span class="sxs-lookup"><span data-stu-id="b6798-116">Enable and Configure FILESTREAM</span></span>](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
