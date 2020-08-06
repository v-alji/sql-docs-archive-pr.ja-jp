---
title: 暗号化された列のデータをレプリケートする (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e1528d81faa352fdcdf37abe9ad93fda190445c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716246"
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a><span data-ttu-id="e201e-102">暗号化された列のデータをレプリケートする (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e201e-102">Replicate Data in Encrypted Columns (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e201e-103">レプリケーションでは、暗号化された列データをパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="e201e-103">Replication enables you to publish encrypted column data.</span></span> <span data-ttu-id="e201e-104">このデータの暗号化を解除してサブスクライバーで使用するには、パブリッシャーでのデータの暗号化に使用されたキーがサブスクライバーにも存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e201e-104">To decrypt and use this data at the Subscriber, the key that was used to encrypt the data at the Publisher must also be present on the Subscriber.</span></span> <span data-ttu-id="e201e-105">レプリケーションでは、暗号化キーを送信する安全なメカニズムは提供されません。</span><span class="sxs-lookup"><span data-stu-id="e201e-105">Replication does not provide a secure mechanism to transport encryption keys.</span></span> <span data-ttu-id="e201e-106">このため、暗号化キーはサブスクライバーで手動で再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e201e-106">You must manually re-create the encryption key at the Subscriber.</span></span> <span data-ttu-id="e201e-107">このトピックでは、パブリッシャーで列を暗号化し、暗号化キーをサブスクライバーで使用できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e201e-107">This topic shows you how to encrypt a column at the Publisher and make sure that the encryption key is available at the Subscriber.</span></span>  
  
 <span data-ttu-id="e201e-108">基本的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e201e-108">The basic steps are as follows:</span></span>  
  
1.  <span data-ttu-id="e201e-109">パブリッシャーで対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e201e-109">Create the symmetric key at the Publisher.</span></span>  
  
2.  <span data-ttu-id="e201e-110">その対称キーを使用して列データを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="e201e-110">Encrypt column data with the symmetric key.</span></span>  
  
3.  <span data-ttu-id="e201e-111">暗号化された列を含むテーブルをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="e201e-111">Publish the table with the encrypted column.</span></span>  
  
4.  <span data-ttu-id="e201e-112">パブリケーションにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e201e-112">Subscribe to the publication.</span></span>  
  
5.  <span data-ttu-id="e201e-113">サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="e201e-113">Initialize the subscription.</span></span>  
  
6.  <span data-ttu-id="e201e-114">手順 1 と同じ値を ALGORITHM、KEY_SOURCE、IDENTITY_VALUE に使用して、サブスクライバーで対称キーを再作成します。</span><span class="sxs-lookup"><span data-stu-id="e201e-114">Recreate the symmetric key at the Subscriber using same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span>  
  
7.  <span data-ttu-id="e201e-115">暗号化された列データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e201e-115">Access the encrypted column data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e201e-116">列データを暗号化するには、対称キーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e201e-116">You should use a symmetric key to encrypt column data.</span></span> <span data-ttu-id="e201e-117">対称キー自体は、パブリッシャーとサブスクライバーで、それぞれ異なる手段で保護できます。</span><span class="sxs-lookup"><span data-stu-id="e201e-117">The symmetric key itself can be secured by different means at the Publisher and Subscriber.</span></span>  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a><span data-ttu-id="e201e-118">暗号化された列データを作成およびレプリケートするには</span><span class="sxs-lookup"><span data-stu-id="e201e-118">To create and replicate encrypted column data</span></span>  
  
1.  <span data-ttu-id="e201e-119">パブリッシャーで、 [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="e201e-119">At the Publisher, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e201e-120">KEY_SOURCE の値は、対象キーの再作成およびデータの暗号化解除に使用できる重要なデータです。</span><span class="sxs-lookup"><span data-stu-id="e201e-120">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="e201e-121">KEY_SOURCE は、常に安全に格納および送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e201e-121">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
2.  <span data-ttu-id="e201e-122">[OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) を実行して新しいキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e201e-122">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
3.  <span data-ttu-id="e201e-123">[EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) 関数を使用して、パブリッシャーで列データを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="e201e-123">Use the [EncryptByKey](/sql/t-sql/functions/encryptbykey-transact-sql) function to encrypt column data at the Publisher.</span></span>  
  
4.  <span data-ttu-id="e201e-124">[CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) を実行してキーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e201e-124">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
5.  <span data-ttu-id="e201e-125">暗号化された列を含むテーブルをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="e201e-125">Publish the table that contains the encrypted column.</span></span> <span data-ttu-id="e201e-126">詳しくは、「 [パブリケーションを作成](../publish/create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e201e-126">For more information, see [Create a Publication](../publish/create-a-publication.md).</span></span>  
  
6.  <span data-ttu-id="e201e-127">パブリケーションにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="e201e-127">Subscribe to the publication.</span></span> <span data-ttu-id="e201e-128">詳細については、「[プル サブスクリプションの作成](../create-a-pull-subscription.md)」または「[プッシュ サブスクリプションの作成](../create-a-push-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e201e-128">For more information, see [Create a Pull Subscription](../create-a-pull-subscription.md) or [Create a Push Subscription](../create-a-push-subscription.md).</span></span>  
  
7.  <span data-ttu-id="e201e-129">サブスクリプションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="e201e-129">Initialize the subscription.</span></span> <span data-ttu-id="e201e-130">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e201e-130">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
8.  <span data-ttu-id="e201e-131">手順 1 と同じ値を ALGORITHM、KEY_SOURCE、および IDENTITY_VALUE に使用して、サブスクライバーで [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="e201e-131">At the Subscriber, execute [CREATE SYMMETRIC KEY](/sql/t-sql/statements/create-symmetric-key-transact-sql) using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE as in step 1.</span></span> <span data-ttu-id="e201e-132">ENCRYPTION BY には別の値を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e201e-132">You can specify a different value for ENCRYPTION BY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e201e-133">KEY_SOURCE の値は、対象キーの再作成およびデータの暗号化解除に使用できる重要なデータです。</span><span class="sxs-lookup"><span data-stu-id="e201e-133">The value of KEY_SOURCE is valuable data that can be used to re-create the symmetric key and decrypt data.</span></span> <span data-ttu-id="e201e-134">KEY_SOURCE は、常に安全に格納および送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e201e-134">KEY_SOURCE must always be stored and transported securely.</span></span>  
  
9. <span data-ttu-id="e201e-135">[OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) を実行して新しいキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e201e-135">Execute [OPEN SYMMETRIC KEY](/sql/t-sql/statements/open-symmetric-key-transact-sql) to open the new key.</span></span>  
  
10. <span data-ttu-id="e201e-136">[DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) 関数を使用して、サブスクライバーでレプリケートされたデータを暗号解除します。</span><span class="sxs-lookup"><span data-stu-id="e201e-136">Use the [DecryptByKey](/sql/t-sql/functions/decryptbykey-transact-sql) function to decrypt replicated data at the Subscriber.</span></span>  
  
11. <span data-ttu-id="e201e-137">[CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) を実行してキーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e201e-137">Execute [CLOSE SYMMETRIC KEY](/sql/t-sql/statements/close-symmetric-key-transact-sql) to close the key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e201e-138">例</span><span class="sxs-lookup"><span data-stu-id="e201e-138">Example</span></span>  
 <span data-ttu-id="e201e-139">この例では、対称キー、対称キーを保護するために使用される証明書、およびマスター キーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="e201e-139">This example creates a symmetric key, a certificate that is used to help secure the symmetric key, and a master key.</span></span> <span data-ttu-id="e201e-140">これらのキーは、パブリケーション データベースで作成されます。</span><span class="sxs-lookup"><span data-stu-id="e201e-140">These keys are created in the publication database.</span></span> <span data-ttu-id="e201e-141">これらは、 `SalesOrderHeader` テーブル内の暗号化された列 (EncryptedCreditCardApprovalCode) の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e201e-141">They are then used to create an encrypted column (EncryptedCreditCardApprovalCode) in the `SalesOrderHeader` table.</span></span> <span data-ttu-id="e201e-142">この列は、暗号化していない CreditCardApprovalCode 列の代わりに、AdvWorksSalesOrdersMerge パブリケーションでパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="e201e-142">This column is published in the AdvWorksSalesOrdersMerge publication instead of the unencrypted CreditCardApprovalCode column.</span></span> <span data-ttu-id="e201e-143">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="e201e-143">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="e201e-144">スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="e201e-144">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/publishencryptedcolumn.sql#sp_publishencryptedcolumn)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="example"></a><span data-ttu-id="e201e-145">例</span><span class="sxs-lookup"><span data-stu-id="e201e-145">Example</span></span>  
 <span data-ttu-id="e201e-146">この例では、最初の例の ALGORITHM、KEY_SOURCE、および IDENTITY_VALUE の場合と同じ値を使用して、サブスクリプション データベース内に同じ対象キーを再作成しています。</span><span class="sxs-lookup"><span data-stu-id="e201e-146">This example recreates the same symmetric key in the subscription database using the same values for ALGORITHM, KEY_SOURCE, and IDENTITY_VALUE from the first example.</span></span> <span data-ttu-id="e201e-147">この例は、暗号化された列をレプリケートする AdvWorksSalesOrdersMerge パブリケーションへのサブスクリプションが初期化済みであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e201e-147">This example assumes that you have already initialized a subscription to the AdvWorksSalesOrdersMerge publication to replicate the encrypted column.</span></span> <span data-ttu-id="e201e-148">可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。</span><span class="sxs-lookup"><span data-stu-id="e201e-148">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="e201e-149">スクリプト ファイルに資格情報を保存する必要がある場合は、格納時および送信時の不正アクセスからファイルを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e201e-149">If you must store credentials in a script file, you must secure the file during storage and transport to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../snippets/tsql/SQL15/replication/howto/tsql/subscriberencryptedcolumn.sql#sp_subscriberencryptedcolumn)]  
  
## <a name="see-also"></a><span data-ttu-id="e201e-150">参照</span><span class="sxs-lookup"><span data-stu-id="e201e-150">See Also</span></span>  
 <span data-ttu-id="e201e-151">[SQL Server レプリケーションのセキュリティ](view-and-modify-replication-security-settings.md) </span><span class="sxs-lookup"><span data-stu-id="e201e-151">[SQL Server Replication Security](view-and-modify-replication-security-settings.md) </span></span>  
 [<span data-ttu-id="e201e-152">2 台のサーバーでの同じ対称キーの作成</span><span class="sxs-lookup"><span data-stu-id="e201e-152">Create Identical Symmetric Keys on Two Servers</span></span>](../../security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
