sequenceDiagram
    title Library Management System - Odunc Alma

    actor Uye
    participant LC as Library Controller
    participant LoanService as Loan Service
    participant BookRepo as Book Repository
    participant LoanRepo as Loan Repository

    Uye ->> LC: odunc_al(isbn)
    LC ->> LoanService: func()

    LoanService ->> BookRepo: kitap_getir(param)
    BookRepo -->> LoanService: kitap

    LoanService ->> LoanService: uygun_mu()

    LoanService ->> LoanRepo: odunc_kaydi_olustur(uye_id, isbn)
    LoanRepo -->> LoanService: odunc_kaydi

    LoanService ->> BookRepo: kitap_durum_guncelle(isbn, oduncte)

    LoanService -->> LC: basarili
    LC -->> Uye: odunc islemi tamamlandi
