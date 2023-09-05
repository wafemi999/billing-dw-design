
BEGIN;


CREATE TABLE public."FactBilling"
(
    rowid integer NOT NULL,
    customerid integer NOT NULL,
    monthid integer NOT NULL,
    billedamount integer NOT NULL,
    PRIMARY KEY (rowid)
);

CREATE TABLE public."DimMonth"
(
    monthid integer NOT NULL,
    year integer NOT NULL,
    month integer NOT NULL,
    monthname "char" NOT NULL,
    quarter integer NOT NULL,
    quartername "char" NOT NULL,
    PRIMARY KEY (monthid)
);

CREATE TABLE public."DimCustomer"
(
    customerid integer NOT NULL,
    category "char" NOT NULL,
    country "char" NOT NULL,
    industry "char" NOT NULL,
    PRIMARY KEY (customerid)
);

ALTER TABLE public."FactBilling"
    ADD FOREIGN KEY (customerid)
    REFERENCES public."DimCustomer" (customerid)
    NOT VALID;


ALTER TABLE public."FactBilling"
    ADD FOREIGN KEY (monthid)
    REFERENCES public."DimMonth" (monthid)
    NOT VALID;

END;