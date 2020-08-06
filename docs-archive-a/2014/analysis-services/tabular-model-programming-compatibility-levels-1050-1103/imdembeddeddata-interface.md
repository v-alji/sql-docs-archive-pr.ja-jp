---
title: IMDEmbedded Interface |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 9dba8c68-4bef-4c2b-815c-c286f1a1939b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 331f8c33f7748e6591acd6d6ecda7a03ef7d8137
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634690"
---
# <a name="imdembedded-interface"></a><span data-ttu-id="acc70-102">IMDEmbedded インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acc70-102">IMDEmbedded Interface</span></span>
  <span data-ttu-id="acc70-103">IMDEmbedded インターフェイスは、埋め込みの PowerPivot データベースまたはテーブル モデル データベースを管理するために使用されるパブリック インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="acc70-103">The IMDEmbedded interface is a public interface used to manage an embedded PowerPivot database or a tabular model database.</span></span> <span data-ttu-id="acc70-104">このインターフェイスは、`IPersistStream` インターフェイスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="acc70-104">The interface inherits from the `IPersistStream` interface.</span></span> <span data-ttu-id="acc70-105">このインターフェイスでは、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="acc70-105">The interface allows for the following operations:</span></span>  
  
-   <span data-ttu-id="acc70-106">コンテナー ドキュメント内の埋め込みストリームの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="acc70-106">Get an identifier to the embedded stream in the container document.</span></span>  
  
-   <span data-ttu-id="acc70-107">ドキュメントの URL を設定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-107">Set the URL of the containing document.</span></span>  
  
-   <span data-ttu-id="acc70-108">埋め込みアプリケーションがホスト環境にあるかどうかを示すフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-108">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
-   <span data-ttu-id="acc70-109">埋め込みアプリケーションが使用する一時ファイルのパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-109">Set the path to temporary files used by the embedding application.</span></span>  
  
-   <span data-ttu-id="acc70-110">現在の埋め込み操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="acc70-110">Cancel the current embedded operation.</span></span>  
  
-   <span data-ttu-id="acc70-111">埋め込みオブジェクトを保存するストリームの推定サイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="acc70-111">Get the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="acc70-112">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-112">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="acc70-113">埋め込みデータベースが最後に保存されてから変更されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="acc70-113">Verify if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="acc70-114">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-114">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="acc70-115">ローカルまたはインプロセスエンジンに埋め込みデータベースを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="acc70-115">Load the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="acc70-116">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-116">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="acc70-117">ローカルまたはインプロセス データベースをコンテナー ドキュメント内の埋め込みストリームに保存します。</span><span class="sxs-lookup"><span data-stu-id="acc70-117">Save the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="acc70-118">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-118">Inherited from `IPersistStream`.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="acc70-119">リファレンス</span><span class="sxs-lookup"><span data-stu-id="acc70-119">Reference</span></span>  
 <span data-ttu-id="acc70-120">次のリファレンスでは、 `IMDEmbedded` **msmd.h**ヘッダーファイルに示されているインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="acc70-120">The following reference documents the `IMDEmbedded` interface as presented in **msmd.h** header file.</span></span>  
  
### <a name="source-file-pxoembeddeddataidl"></a><span data-ttu-id="acc70-121">ソース ファイル: PXOEmbeddedData.idl</span><span class="sxs-lookup"><span data-stu-id="acc70-121">Source file: PXOEmbeddedData.idl</span></span>  
  
```  
[  
  local,                            
  object,                           
  uuid(6B6691CF-5453-41c2-ADD9-4F320B7FD421),                       
  pointer_default(unique)           
]  
interface IMDEmbeddedData : IPersistStream  
{  
 [id(1), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in] BOOL in_fIsHosted);  
  
 [id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
  
 [id(3), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
  
 [id(4), helpstring("Set the path used by the embedding application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
  
 [id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
};  
```  
  
### <a name="imdembeddeddatagetstreamidentifier"></a><span data-ttu-id="acc70-122">IMDEmbeddedData::GetStreamIdentifier</span><span class="sxs-lookup"><span data-stu-id="acc70-122">IMDEmbeddedData::GetStreamIdentifier</span></span>  
  
```  
HRESULT GetStreamIdentifier (  
    [out, retval] BSTR * out_pbstrStreamId  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-123">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-123">Description</span></span>  
 <span data-ttu-id="acc70-124">ホスト アプリケーションが使用するコンテナー ドキュメント内の埋め込みストリームの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="acc70-124">Gets the identifier used by the host application to the embedded stream in the container document.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-125">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-125">Parameters</span></span>  
 <span data-ttu-id="acc70-126">*out_pbstrStreamId*</span><span class="sxs-lookup"><span data-stu-id="acc70-126">*out_pbstrStreamId*</span></span>  
 <span data-ttu-id="acc70-127">ストリーム識別子の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-127">Specifies the location of the stream identifier.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="acc70-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-128">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-129">ストリーム識別子が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-129">The stream identifier was successfully returned.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="acc70-130">ストリーム識別子がありません。</span><span class="sxs-lookup"><span data-stu-id="acc70-130">There is no stream identifier.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-131">ストリーム識別子へのアクセス中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-131">An error occurred accessing the stream identifier.</span></span>  
  
#### <a name="remarks"></a><span data-ttu-id="acc70-132">解説</span><span class="sxs-lookup"><span data-stu-id="acc70-132">Remarks</span></span>  
 <span data-ttu-id="acc70-133">現在の接続に埋め込みデータベースが含まれているかどうかを確認するには、OLE DB 接続プロパティから DBPROP_MSMD_EMBEDDED_DATA プロパティの値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="acc70-133">To verify if the current connection contains an embedded database, the user should check the value of the DBPROP_MSMD_EMBEDDED_DATA property from the OLE DB connection properties.</span></span>  
  
 <span data-ttu-id="acc70-134">DBPROP_MSMD_EMBEDDED_DATA は、次のいずれかの値をとります。</span><span class="sxs-lookup"><span data-stu-id="acc70-134">The possible values for DBPROP_MSMD_EMBEDDED_DATA are:</span></span>  
  
|<span data-ttu-id="acc70-135">名前</span><span class="sxs-lookup"><span data-stu-id="acc70-135">Name</span></span>|<span data-ttu-id="acc70-136">値</span><span class="sxs-lookup"><span data-stu-id="acc70-136">Value</span></span>|<span data-ttu-id="acc70-137">定義</span><span class="sxs-lookup"><span data-stu-id="acc70-137">Definition</span></span>|  
|----------|-----------|----------------|  
|<span data-ttu-id="acc70-138">DBPROPVAL_EMBED_NONE</span><span class="sxs-lookup"><span data-stu-id="acc70-138">DBPROPVAL_EMBED_NONE</span></span>|<span data-ttu-id="acc70-139">0x00</span><span class="sxs-lookup"><span data-stu-id="acc70-139">0x00</span></span>|<span data-ttu-id="acc70-140">使用できる埋め込みデータベースがありません。</span><span class="sxs-lookup"><span data-stu-id="acc70-140">No embedded database available</span></span>|  
|<span data-ttu-id="acc70-141">DBPROPVAL_EMBED_EMBEDDED</span><span class="sxs-lookup"><span data-stu-id="acc70-141">DBPROPVAL_EMBED_EMBEDDED</span></span>|<span data-ttu-id="acc70-142">0x01</span><span class="sxs-lookup"><span data-stu-id="acc70-142">0x01</span></span>|<span data-ttu-id="acc70-143">現在のアプリケーションには埋め込みデータベースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="acc70-143">The current application contains the embedded database</span></span>|  
|<span data-ttu-id="acc70-144">DBPROPVAL_EMBED_LINKED</span><span class="sxs-lookup"><span data-stu-id="acc70-144">DBPROPVAL_EMBED_LINKED</span></span>|<span data-ttu-id="acc70-145">0x02</span><span class="sxs-lookup"><span data-stu-id="acc70-145">0x02</span></span>|<span data-ttu-id="acc70-146">埋め込みデータベースはリモート アプリケーション (SharePoint Server など) でホストされています。</span><span class="sxs-lookup"><span data-stu-id="acc70-146">The embedded database is hosted in a remote application (i.e. SharePoint Server)</span></span>|  
  
#### <a name="source"></a><span data-ttu-id="acc70-147">source</span><span class="sxs-lookup"><span data-stu-id="acc70-147">Source</span></span>  
  
```  
[id(1), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
```  
  
### <a name="imdembeddeddatasetcontainerurl"></a><span data-ttu-id="acc70-148">IMDEmbeddedData::SetContainerURL</span><span class="sxs-lookup"><span data-stu-id="acc70-148">IMDEmbeddedData::SetContainerURL</span></span>  
  
```  
HRESULT SetContainerURL (  
    [in] BSTR in_bstrURL  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-149">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-149">Description</span></span>  
 <span data-ttu-id="acc70-150">埋め込みストリームが含まれているファイルの URL を設定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-150">Sets the URL for the file containing the embedded stream.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-151">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-151">Parameters</span></span>  
 <span data-ttu-id="acc70-152">*in_bstrURL*</span><span class="sxs-lookup"><span data-stu-id="acc70-152">*in_bstrURL*</span></span>  
 <span data-ttu-id="acc70-153">ドキュメントの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-153">Specifies the URL for the containing document.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="acc70-154">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-154">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-155">コンテナー URL は正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-155">The container URL was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-156">コンテナー URL の設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-156">An error occurred while setting the container URL.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="acc70-157">source</span><span class="sxs-lookup"><span data-stu-id="acc70-157">Source</span></span>  
  
```  
[id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
```  
  
### <a name="imdembeddeddatasethosted"></a><span data-ttu-id="acc70-158">IMDEmbeddedData::SetHosted</span><span class="sxs-lookup"><span data-stu-id="acc70-158">IMDEmbeddedData::SetHosted</span></span>  
  
```  
HRESULT SetHosted (  
    [in] BOOL in_fIsHosted  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-159">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-159">Description</span></span>  
 <span data-ttu-id="acc70-160">埋め込みアプリケーションがホスト環境にあるかどうかを示すフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-160">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-161">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-161">Parameters</span></span>  
 <span data-ttu-id="acc70-162">*in_ftHosted*</span><span class="sxs-lookup"><span data-stu-id="acc70-162">*in_ftHosted*</span></span>  
 <span data-ttu-id="acc70-163">呼び出し元がサービス アプリケーション (IIS など) でホストされている場合は TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="acc70-163">TRUE if caller is in a hosted in a service application (like IIS).</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="acc70-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-164">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-165">フラグは正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-165">The flag was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-166">フラグの設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-166">An error occurred while setting the flag.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="acc70-167">source</span><span class="sxs-lookup"><span data-stu-id="acc70-167">Source</span></span>  
  
```  
[id(5), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in]  BOOL in_fIsHosted);  
```  
  
### <a name="imdembeddeddatasettempdirpath"></a><span data-ttu-id="acc70-168">IMDEmbeddedData::SetTempDirPath</span><span class="sxs-lookup"><span data-stu-id="acc70-168">IMDEmbeddedData::SetTempDirPath</span></span>  
  
```  
HRESULT SetTempDirPath (  
    [in] BSTR in_bstrPath  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-169">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-169">Description</span></span>  
 <span data-ttu-id="acc70-170">埋め込みアプリケーションが使用する一時ファイルのパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="acc70-170">Set the path to temporary files used by the embedding application.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-171">Parameters</span></span>  
 <span data-ttu-id="acc70-172">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="acc70-172">*in_bstrPath*</span></span>  
 <span data-ttu-id="acc70-173">ホスト アプリケーションが一時ファイルに使用するパス。</span><span class="sxs-lookup"><span data-stu-id="acc70-173">The path used by the host application for temporary files.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="acc70-174">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-174">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-175">一時ファイルのディレクトリは正常に設定されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-175">The temporary file directory was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-176">パスの設定中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-176">An error occurred while setting the path.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="acc70-177">source</span><span class="sxs-lookup"><span data-stu-id="acc70-177">Source</span></span>  
  
```  
[id(4), helpstring("Set the path used by the host application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
```  
  
### <a name="imdembeddeddatacancel"></a><span data-ttu-id="acc70-178">IMDEmbeddedData::Cancel</span><span class="sxs-lookup"><span data-stu-id="acc70-178">IMDEmbeddedData::Cancel</span></span>  
  
```  
HRESULT Cancel ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-179">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-179">Description</span></span>  
 <span data-ttu-id="acc70-180">現在の埋め込みデータベース操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="acc70-180">Cancels the current embedded database operation</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-181">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-181">Parameters</span></span>  
 <span data-ttu-id="acc70-182">[なし] :</span><span class="sxs-lookup"><span data-stu-id="acc70-182">None.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="acc70-183">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-183">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-184">操作が正常に取り消されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-184">The operation was successfully cancelled.</span></span>  
  
 `DB_E_CANTCANCEL`  
 <span data-ttu-id="acc70-185">現在実行中の取り消し可能な操作はありません。</span><span class="sxs-lookup"><span data-stu-id="acc70-185">No cancellable operation is currently in progress.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-186">埋め込み操作の取り消し中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-186">An error occurred while cancelling the embedded operation.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="acc70-187">source</span><span class="sxs-lookup"><span data-stu-id="acc70-187">Source</span></span>  
  
```  
[id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
```  
  
### <a name="imdembeddeddatagetsizemax-ipersiststreamgetsizemax"></a><span data-ttu-id="acc70-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span><span class="sxs-lookup"><span data-stu-id="acc70-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span></span>  
  
```  
HRESULT GetSizeMax (  
    [out] ULARGE_INTEGER * out_pcbSize  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-189">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-189">Description</span></span>  
 <span data-ttu-id="acc70-190">ストリームの推定サイズ (バイト単位) を取得し、埋め込みオブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="acc70-190">Gets the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="acc70-191">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-191">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-192">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-192">Parameters</span></span>  
 <span data-ttu-id="acc70-193">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="acc70-193">*in_bstrPath*</span></span>  
 <span data-ttu-id="acc70-194">埋め込みデータベース イメージの推定サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="acc70-194">The estimated size (in bytes) of the embedded database image.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="acc70-195">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-195">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-196">サイズは正常に取得されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-196">The size was successfully obtained.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-197">サイズの取得中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-197">An error occurred while obtaining the size.</span></span>  
  
### <a name="imdembeddeddataisdirty-ipersiststreamisdirty"></a><span data-ttu-id="acc70-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span><span class="sxs-lookup"><span data-stu-id="acc70-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span></span>  
  
```  
HRESULT IsDirty ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-199">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-199">Description</span></span>  
 <span data-ttu-id="acc70-200">埋め込みデータベースが最後に保存されてから変更されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="acc70-200">Verifies if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="acc70-201">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-201">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-202">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-202">Parameters</span></span>  
 <span data-ttu-id="acc70-203">なし</span><span class="sxs-lookup"><span data-stu-id="acc70-203">none</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="acc70-204">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-204">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-205">データベースは最後に保存されてから変更されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-205">The database has changed since it was last saved.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="acc70-206">データベースは最後に保存されてから変更されていません。</span><span class="sxs-lookup"><span data-stu-id="acc70-206">The database has not changed since it was last saved.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-207">データベース状態の取得中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="acc70-207">An error occurred while obtaining the database state.</span></span>  
  
### <a name="imdembeddeddataload-ipersiststreamload"></a><span data-ttu-id="acc70-208">IMDEmbeddedData::Load (IPersistStream::Load)</span><span class="sxs-lookup"><span data-stu-id="acc70-208">IMDEmbeddedData::Load (IPersistStream::Load)</span></span>  
  
```  
HRESULT Load (   
    [in] IStream * in_pStm   
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-209">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-209">Description</span></span>  
 <span data-ttu-id="acc70-210">埋め込みデータベースをローカルまたはインプロセス エンジンに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="acc70-210">Loads the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="acc70-211">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-211">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-212">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-212">Parameters</span></span>  
 <span data-ttu-id="acc70-213">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="acc70-213">*in_pStm*</span></span>  
 <span data-ttu-id="acc70-214">埋め込みデータベースを読み込むストリーム インターフェイスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="acc70-214">A pointer to a stream interface from where to load the embedded database.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="acc70-215">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-215">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-216">データベースは正常に読み込まれました。</span><span class="sxs-lookup"><span data-stu-id="acc70-216">The database was successfully loaded.</span></span>  
  
 `E_OUTOFMEMORY`  
 <span data-ttu-id="acc70-217">データベースを読み込むためのメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="acc70-217">Not enough memory to load the database.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="acc70-218">データベースの読み込み中にエラーが発生しました。`E_OUTOFMEMORY` とは異なります。</span><span class="sxs-lookup"><span data-stu-id="acc70-218">An error occurred while loading the database, different than `E_OUTOFMEMORY`.</span></span>  
  
### <a name="imdembeddeddatasave-ipersiststreamsave"></a><span data-ttu-id="acc70-219">IMDEmbeddedData::Save (IPersistStream::Save)</span><span class="sxs-lookup"><span data-stu-id="acc70-219">IMDEmbeddedData::Save (IPersistStream::Save)</span></span>  
  
```  
HRESULT Save (   
    [in] IStream * in_pStm,  
    [in] BOOL in_fClearDirty  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="acc70-220">説明</span><span class="sxs-lookup"><span data-stu-id="acc70-220">Description</span></span>  
 <span data-ttu-id="acc70-221">ローカルまたはプロセス内のデータベースをコンテナードキュメント内の埋め込みストリームに保存します。</span><span class="sxs-lookup"><span data-stu-id="acc70-221">Saves the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="acc70-222">このプロパティは、`IPersistStream` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="acc70-222">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="acc70-223">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acc70-223">Parameters</span></span>  
 <span data-ttu-id="acc70-224">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="acc70-224">*in_pStm*</span></span>  
 <span data-ttu-id="acc70-225">埋め込みデータベースの保存先のストリーム インターフェイスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="acc70-225">A pointer to a stream interface to where to save the embedded database.</span></span>  
  
 <span data-ttu-id="acc70-226">*in_fClearDirty*</span><span class="sxs-lookup"><span data-stu-id="acc70-226">*in_fClearDirty*</span></span>  
 <span data-ttu-id="acc70-227">この操作の後にダーティ フラグを消去する必要があるかどうかを示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="acc70-227">A flag that indicates whether the dirty flag should be cleared after this operation.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="acc70-228">戻り値</span><span class="sxs-lookup"><span data-stu-id="acc70-228">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="acc70-229">データベースは正常に保存されました。</span><span class="sxs-lookup"><span data-stu-id="acc70-229">The database was successfully saved.</span></span>  
  
 `STG_E_CANTSAVE`  
 <span data-ttu-id="acc70-230">データベースの保存中にエラーが発生しました。`STG_E_MEDIUMFULL` とは異なります。</span><span class="sxs-lookup"><span data-stu-id="acc70-230">An error occurred while saving the database, different than `STG_E_MEDIUMFULL`.</span></span>  
  
 `STG_E_MEDIUMFULL`  
 <span data-ttu-id="acc70-231">ストレージ デバイスに空き領域がないため、データベースを保存できませんでした。</span><span class="sxs-lookup"><span data-stu-id="acc70-231">The database could not be saved because there is no space left on the storage device.</span></span>  
  
  
