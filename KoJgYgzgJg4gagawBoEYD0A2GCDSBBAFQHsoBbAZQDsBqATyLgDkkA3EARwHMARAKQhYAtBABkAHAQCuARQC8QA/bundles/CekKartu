function cetak_KartuVaksinasi(n) {
    var i = $("#CaptchaInputText").val(),
        t = $("#CaptchaInputText").get(0).Captcha,
        r = t.Id,
        u = t.InstanceId,
        f = $("#nik").val(),
        e = {
            CaptchaInputText: i,
            captchaid: r,
            instanceid: u,
            NoRegister: n,
            NIK: f
        },
        o = LZString.compressToEncodedURIComponent(JSON.stringify(e));
    $.ajax({
        url: base_url + "https://pcare.bpjs-kesehatan.go.id/KartuVaksin/CekKartu",
        data: JSON.stringify({
            data: enkripdekrip.tutup(o, Config.kode)
        }),
        contentType: "application/json",
        type: "POST",
        success: function(n) {
            if (n.metaData.code === 200) {
                var i = n.response.list[0];
                i.kartuVaksinasi.noTiket != null ? CreatePDF_KartuVaksinasi(i, 2) : ($("#nik").val(""), ShareMethod.showMessage(500, "Maaf Saat Ini Server Sedang Maintenance!"))
            } else $("#nik").val(""), ShareMethod.showMessage(n.metaData.code, n.metaData.message);
            t.ReloadImage()
        },
        error: function(n) {
            errorHandler(n.responseJSON)
        }
    })
}
let id, nm;
$(document).ready(function() {
    $("a[title ~= 'BotDetect']").removeAttr("style");
    $("a[title ~= 'BotDetect']").removeAttr("href");
    $("a[title ~= 'BotDetect']").css("visibility", "hidden");
    $("#btnCek").click(function() {
        for (var n = [], t, r = window.location.href.slice(window.location.href.indexOf("?") + 1).split("&"), i = 0; i < r.length; i++) t = r[i].split("="), n.push(t[0]), n[t[0]] = t[1];
        n.r != undefined && n.i != undefined ? cetak_KartuVaksinasi(n.i) : ShareMethod.showMessage(500, "Maaf Saat Ini Server Sedang Maintenance!")
    })
})
