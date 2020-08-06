---
title: clr enabled サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- assemblies [CLR integration], verifying can run
- clr enabled option
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b83cd0e00bdd32c8b44667209544c8e81b1e90c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632108"
---
# <a name="clr-enabled-server-configuration-option"></a><span data-ttu-id="cdc28-102">clr enabled サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="cdc28-102">clr enabled Server Configuration Option</span></span>
  <span data-ttu-id="cdc28-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でユーザー アセンブリを実行できるかどうかを指定するには、clr enabled オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdc28-103">Use the clr enabled option to specify whether user assemblies can be run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cdc28-104">clr enabled オプションでは、次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="cdc28-104">The clr enabled option provides the following values.</span></span>  
  
|<span data-ttu-id="cdc28-105">値</span><span class="sxs-lookup"><span data-stu-id="cdc28-105">Value</span></span>|<span data-ttu-id="cdc28-106">説明</span><span class="sxs-lookup"><span data-stu-id="cdc28-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cdc28-107">0</span><span class="sxs-lookup"><span data-stu-id="cdc28-107">0</span></span>|<span data-ttu-id="cdc28-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でアセンブリを実行できません。</span><span class="sxs-lookup"><span data-stu-id="cdc28-108">Assembly execution not allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="cdc28-109">1</span><span class="sxs-lookup"><span data-stu-id="cdc28-109">1</span></span>|<span data-ttu-id="cdc28-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でアセンブリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cdc28-110">Assembly execution allowed on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
 <span data-ttu-id="cdc28-111">WOW64 サーバーの場合、この設定に対する変更を有効にするには再起動が必要です。</span><span class="sxs-lookup"><span data-stu-id="cdc28-111">WOW64 servers must be restarted before the changes to this setting will take effect.</span></span> <span data-ttu-id="cdc28-112">他の種類のサーバーでは、再起動は不要です。</span><span class="sxs-lookup"><span data-stu-id="cdc28-112">Restart is not required for other server types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cdc28-113">RECONFIGURE が実行され、clr enabled オプションの実行値が 1 から 0 に変更されると、ユーザー アセンブリが含まれているすべてのアプリケーション ドメインが直ちにアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="cdc28-113">When RECONFIGURE is run and the run value of the clr enabled option is changed from 1 to 0, all application domains containing user assemblies are immediately unloaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cdc28-114">簡易プーリングでは、共通言語ランタイム (CLR) の実行はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cdc28-114">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="cdc28-115">"Clr enabled" または "簡易プーリング" の2つのオプションのいずれかを無効にします。</span><span class="sxs-lookup"><span data-stu-id="cdc28-115">Disable one of two options: "clr enabled" or "lightweight pooling.</span></span> <span data-ttu-id="cdc28-116">CLR に依存していてファイバー モードで正しく動作しない機能には、`hierarchy` データ型、レプリケーション、およびポリシー ベースの管理があります。</span><span class="sxs-lookup"><span data-stu-id="cdc28-116">Features that rely upon CLR and that do not work properly in fiber mode include the `hierarchy` data type, replication, and Policy-Based Management.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdc28-117">例</span><span class="sxs-lookup"><span data-stu-id="cdc28-117">Example</span></span>  
 <span data-ttu-id="cdc28-118">次の例では、最初に clr enabled オプションの現在の設定を表示し、その後、オプションの値を 1 に設定することで、このオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cdc28-118">The following example first displays the current setting of the clr enabled option and then enables the option by setting the option value to 1.</span></span> <span data-ttu-id="cdc28-119">このオプションを無効にするには、値を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="cdc28-119">To disable the option, set the value to 0.</span></span>  
  
```  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdc28-120">参照</span><span class="sxs-lookup"><span data-stu-id="cdc28-120">See Also</span></span>  
 <span data-ttu-id="cdc28-121">[lightweight pooling サーバー構成オプション](lightweight-pooling-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="cdc28-121">[lightweight pooling Server Configuration Option](lightweight-pooling-server-configuration-option.md) </span></span>  
 <span data-ttu-id="cdc28-122">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cdc28-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="cdc28-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cdc28-123">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="cdc28-124">lightweight pooling サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="cdc28-124">lightweight pooling Server Configuration Option</span></span>](lightweight-pooling-server-configuration-option.md)  
  
  
