---
title: 米国英語と英国英語に使用されるワード ブレーカーの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3b759b90ec834dcb666f7862bfba3857f2fea0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641582"
---
# <a name="change-the-word-breaker-used-for-us-english-and-uk-english"></a><span data-ttu-id="1dbb2-102">米国英語と英国英語に使用されるワード ブレーカーを変更する方法</span><span class="sxs-lookup"><span data-stu-id="1dbb2-102">Change the Word Breaker Used for US English and UK English</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="1dbb2-103">では、英語用のワード ブレーカーおよびステマーの新しいバージョン (バージョン 14.0.4999.1038) がインストールされて、前のバージョン (バージョン 12.0.6828.0) が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-103">installs a new version (version 14.0.4999.1038) of the word breaker and stemmer for the English language, replacing the previous version of these components (version 12.0.6828.0).</span></span> <span data-ttu-id="1dbb2-104">新しいコンポーネントで変更された動作の詳細については、「 [フルテキスト検索の動作の変更](full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-104">For information about the changed behavior of the new components, see [Behavior Changes to Full-Text Search](full-text-search.md).</span></span> <span data-ttu-id="1dbb2-105">このトピックでは、これらのコンポーネントの新しいバージョンを前のバージョンに切り替えたり、前のバージョンから新しいバージョンに切り替えたりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-105">This topic describes how to switch from the new version of these components to the previous version, or to switch back from the previous version to the new version.</span></span> <span data-ttu-id="1dbb2-106">クラスターのインストールでは、これらの変更を、すべてのプライマリ ノードとパッシブ ノードで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-106">For cluster installations, these changes should be made on all the primary and passive nodes.</span></span>  
  
 <span data-ttu-id="1dbb2-107">前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、米国英語 (LCID 1033) と英国英語 (LCID 2057) に対し、異なる CLSID で表される異なるワード ブレーカーが使用されていました。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-107">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] used different word breakers represented by different CLSIDs for US English (LCID 1033) and UK English (LCID 2057).</span></span> <span data-ttu-id="1dbb2-108">このリリースでは、次の表に示すように、両方の LCID で同じ CLSID を持つ同じコンポーネントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-108">In this release, both LCIDs use the same components with the same CLSIDs, as shown in the following table:</span></span>  
  
|<span data-ttu-id="1dbb2-109">LCID</span><span class="sxs-lookup"><span data-stu-id="1dbb2-109">LCID</span></span>|<span data-ttu-id="1dbb2-110">以前のバージョンでインストールされたワード ブレーカー</span><span class="sxs-lookup"><span data-stu-id="1dbb2-110">Word breaker installed by previous versions</span></span><br /><br /> <span data-ttu-id="1dbb2-111">バージョン 12.0.6828.0</span><span class="sxs-lookup"><span data-stu-id="1dbb2-111">version 12.0.6828.0</span></span>|<span data-ttu-id="1dbb2-112">以前のバージョンでインストールされたステマー</span><span class="sxs-lookup"><span data-stu-id="1dbb2-112">Stemmer installed by previous versions</span></span>|<span data-ttu-id="1dbb2-113">このバージョンでインストールされるワード ブレーカー</span><span class="sxs-lookup"><span data-stu-id="1dbb2-113">Word breaker installed by this version</span></span><br /><br /> <span data-ttu-id="1dbb2-114">バージョン 14.0.4999.1038</span><span class="sxs-lookup"><span data-stu-id="1dbb2-114">version 14.0.4999.1038</span></span>|<span data-ttu-id="1dbb2-115">このバージョンでインストールされるステマー</span><span class="sxs-lookup"><span data-stu-id="1dbb2-115">Stemmer installed by this version</span></span>|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|<span data-ttu-id="1dbb2-116">1033</span><span class="sxs-lookup"><span data-stu-id="1dbb2-116">1033</span></span><br /><span data-ttu-id="1dbb2-117">(米国英語)</span><span class="sxs-lookup"><span data-stu-id="1dbb2-117">(US English)</span></span>|<span data-ttu-id="1dbb2-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span><span class="sxs-lookup"><span data-stu-id="1dbb2-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span></span>|<span data-ttu-id="1dbb2-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="1dbb2-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="1dbb2-120">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="1dbb2-120">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="1dbb2-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="1dbb2-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
|<span data-ttu-id="1dbb2-122">2057</span><span class="sxs-lookup"><span data-stu-id="1dbb2-122">2057</span></span><br /><span data-ttu-id="1dbb2-123">(英国英語)</span><span class="sxs-lookup"><span data-stu-id="1dbb2-123">(UK English)</span></span>|<span data-ttu-id="1dbb2-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span><span class="sxs-lookup"><span data-stu-id="1dbb2-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span></span>|<span data-ttu-id="1dbb2-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="1dbb2-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="1dbb2-126">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="1dbb2-126">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="1dbb2-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="1dbb2-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
  
 <span data-ttu-id="1dbb2-128">このトピックで説明するコンポーネントは、 `MSSQL\Binn` インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フォルダーにインストールされる DLL ファイルです。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-128">The components described in this topic are DLL files that are installed in the `MSSQL\Binn` folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="1dbb2-129">通常、完全なパスは `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`です。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-129">The full path is typically `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.</span></span>  
  
 <span data-ttu-id="1dbb2-130">ワード ブレーカーとステマーの詳細については、「 [検索用のワード ブレーカーとステミング機能の構成と管理](configure-and-manage-word-breakers-and-stemmers-for-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-130">For more information about word breakers and stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="switching-from-the-current-english-word-breaker-to-the-previous-english-word-breakers"></a><span data-ttu-id="1dbb2-131">現在の英語用ワード ブレーカーから前の英語用ワード ブレーカーへの切り替え</span><span class="sxs-lookup"><span data-stu-id="1dbb2-131">Switching from the current English word breaker to the previous English word breakers</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-us-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="1dbb2-132">米国英語用のワード ブレーカーを現在のバージョンから前のバージョンに切り替えるには</span><span class="sxs-lookup"><span data-stu-id="1dbb2-132">To switch from the current version of the US English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="1dbb2-133">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-133">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="1dbb2-134">次の手順を使用して、LCID 1033 の前の米国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-134">Use the following steps to add new keyS for the COM ClassIDs for the previous US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="1dbb2-135">前のワード ブレーカー用に値が **{188D6CC5-CB03-4C01-912E-47D21295D77E}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-135">Add a new key with the value **{188D6CC5-CB03-4C01-912E-47D21295D77E}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="1dbb2-136">このキー値の [(既定)] のデータを **langwrbk.dll**に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-136">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="1dbb2-137">前のステマー用に値が **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-137">Add a new key with the value **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="1dbb2-138">このキー値の [(既定)] のデータを **infosoft.dll** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-138">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="1dbb2-139">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-139">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu**.</span></span>  
  
4.  <span data-ttu-id="1dbb2-140">**WBreakerClass** キー値を **{188D6CC5-CB03-4C01-912E-47D21295D77E}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-140">Update the **WBreakerClass** key value to **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.</span></span>  
  
5.  <span data-ttu-id="1dbb2-141">**StemmerClass** キー値を **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-141">Update the **StemmerClass** key value to **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="1dbb2-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-142">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-uk-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="1dbb2-143">英国英語用のワード ブレーカーを現在のバージョンから前のバージョンに切り替えるには</span><span class="sxs-lookup"><span data-stu-id="1dbb2-143">To switch from the current version of the UK English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="1dbb2-144">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-144">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="1dbb2-145">次の手順を使用して、LCID 2057 の前の英国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-145">Use the following steps to add a new key for the COM ClassIDs for the previous UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="1dbb2-146">前のワード ブレーカー用に値が **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-146">Add a new key with the value **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="1dbb2-147">このキー値の [(既定)] のデータを **langwrbk.dll**に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-147">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="1dbb2-148">前のステマー用に値が **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-148">Add a new key with the value **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="1dbb2-149">このキー値の [(既定)] のデータを **infosoft.dll** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-149">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="1dbb2-150">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-150">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="1dbb2-151">**WBreakerClass** キー値を **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-151">Update the **WBreakerClass** key value to **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.</span></span>  
  
5.  <span data-ttu-id="1dbb2-152">**StemmerClass** キー値を **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-152">Update the **StemmerClass** key value to **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="1dbb2-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-153">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="switching-back-from-the-previous-english-word-breakers-to-the-current-english-word-breaker"></a><span data-ttu-id="1dbb2-154">前の英語用ワード ブレーカーから現在の英語用ワード ブレーカーへの切り替え</span><span class="sxs-lookup"><span data-stu-id="1dbb2-154">Switching back from the previous English word breakers to the current English word breaker</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-us-english-word-breaker-to-the-current-version"></a><span data-ttu-id="1dbb2-155">米国英語用のワード ブレーカーを前のバージョンから現在のバージョンに切り替えるには</span><span class="sxs-lookup"><span data-stu-id="1dbb2-155">To switch back from the previous version of the US English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="1dbb2-156">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-156">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="1dbb2-157">次のキーが存在しない場合は、次の手順を使用して、LCID 1033 の現在の米国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-157">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="1dbb2-158">現在のワード ブレーカー用に値が **{9faed859-0b30-4434-ae65-412e14a16fb8}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-158">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="1dbb2-159">このキー値の [(既定)] のデータを **MsWb7.dll** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-159">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="1dbb2-160">現在のステマー用に値が **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-160">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="1dbb2-161">このキー値の [(既定)] のデータを **MsWb7.dll** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-161">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="1dbb2-162">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-162">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="1dbb2-163">**WBreakerClass** キー値を **{9faed859-0b30-4434-ae65-412e14a16fb8}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-163">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="1dbb2-164">**StemmerClass** キー値を **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-164">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="1dbb2-165">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-165">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-uk-english-word-breaker-to-the-current-version"></a><span data-ttu-id="1dbb2-166">英国英語用のワード ブレーカーを前のバージョンから現在のバージョンに切り替えるには</span><span class="sxs-lookup"><span data-stu-id="1dbb2-166">To switch back from the previous version of the UK English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="1dbb2-167">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-167">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="1dbb2-168">次のキーが存在しない場合は、次の手順を使用して、LCID 2057 の現在の英国英語用ワード ブレーカー インターフェイスおよびステマー インターフェイスに対応する COM ClassID の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-168">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="1dbb2-169">現在のワード ブレーカー用に値が **{9faed859-0b30-4434-ae65-412e14a16fb8}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-169">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="1dbb2-170">このキー値の [(既定)] のデータを **MsWb7.dll** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-170">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="1dbb2-171">現在のステマー用に値が **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** の新しいキーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-171">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="1dbb2-172">このキー値の [(既定)] のデータを **MsWb7.dll** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-172">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="1dbb2-173">レジストリで、**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-173">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="1dbb2-174">**WBreakerClass** キー値を **{9faed859-0b30-4434-ae65-412e14a16fb8}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-174">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="1dbb2-175">**StemmerClass** キー値を **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** に更新します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-175">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="1dbb2-176">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="1dbb2-176">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbb2-177">参照</span><span class="sxs-lookup"><span data-stu-id="1dbb2-177">See Also</span></span>  
 <span data-ttu-id="1dbb2-178">[検索で使用するワード ブレーカーを以前のバージョンに戻す](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span><span class="sxs-lookup"><span data-stu-id="1dbb2-178">[Revert the Word Breakers Used by Search to the Previous Version](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span></span>  
 [<span data-ttu-id="1dbb2-179">フルテキスト検索の動作の変更</span><span class="sxs-lookup"><span data-stu-id="1dbb2-179">Behavior Changes to Full-Text Search</span></span>](full-text-search.md)  
  
  
