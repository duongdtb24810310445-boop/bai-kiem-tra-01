using System;
using System.Collections.Generic;
using System.Linq;

namespace AutoSpeed
{
    // Lop cha truu tuong
    public abstract class PhuongTien
    {
        private string _maPT;
        private string _tenHang;
        private int _namSanXuat;
        private decimal _giaGoc;

        public string MaPT
        {
            get { return _maPT; }
            set
            {
                if (string.IsNullOrWhiteSpace(value))
                    _maPT = "PT000";
                else
                    _maPT = value;
            }
        }

        public string TenHang
        {
            get { return _tenHang; }
            set
            {
                if (string.IsNullOrWhiteSpace(value))
                    throw new ArgumentException("Ten hang khong duoc de trong!");

                _tenHang = value;
            }
        }

        public int NamSanXuat
        {
            get { return _namSanXuat; }
            set
            {
                int namHienTai = DateTime.Now.Year;

                if (value < 1900 || value > namHienTai)
                    throw new ArgumentException("Nam san xuat khong hop le!");

                _namSanXuat = value;
            }
        }

        public decimal GiaGoc
        {
            get { return _giaGoc; }
            set
            {
                if (value <= 0)
                    throw new ArgumentException("Gia goc phai lon hon 0!");

                _giaGoc = value;
            }
        }

        public PhuongTien(
            string maPT,
            string tenHang,
            int namSanXuat,
            decimal giaGoc)
        {
            MaPT = maPT;
            TenHang = tenHang;
            NamSanXuat = namSanXuat;
            GiaGoc = giaGoc;
        }

        public abstract decimal TinhGiaLanBanh();

        public virtual string GetInfo()
        {
            return "Ma PT: " + MaPT
                + " | Hang: " + TenHang
                + " | Nam SX: " + NamSanXuat
                + " | Gia goc: " + GiaGoc.ToString("N0") + " VND";
        }
    }


    // Lop OTo
    public class OTo : PhuongTien
    {
        private int _soChoNgoi;
        private double _dungTichDongCo;

        public int SoChoNgoi
        {
            get { return _soChoNgoi; }
            set
            {
                if (value <= 0)
                    throw new ArgumentException("So cho ngoi phai lon hon 0!");

                _soChoNgoi = value;
            }
        }

        public double DungTichDongCo
        {
            get { return _dungTichDongCo; }
            set
            {
                if (value <= 0)
                    throw new ArgumentException("Dung tich dong co phai lon hon 0!");

                _dungTichDongCo = value;
            }
        }

        public OTo(
            string maPT,
            string tenHang,
            int namSanXuat,
            decimal giaGoc,
            int soChoNgoi,
            double dungTichDongCo)
            : base(maPT, tenHang, namSanXuat, giaGoc)
        {
            SoChoNgoi = soChoNgoi;
            DungTichDongCo = dungTichDongCo;
        }

        public override decimal TinhGiaLanBanh()
        {
            if (SoChoNgoi <= 9)
            {
                return GiaGoc
                    + GiaGoc * 0.12m
                    + GiaGoc * 0.30m;
            }
            else
            {
                return GiaGoc
                    + GiaGoc * 0.10m;
            }
        }

        public override string GetInfo()
        {
            return base.GetInfo()
                + " | So cho: " + SoChoNgoi
                + " | Dung tich dong co: " + DungTichDongCo + " L";
        }
    }


    // Lop XeMay
    public class XeMay : PhuongTien
    {
        private int _dungTichXylanh;

        public int DungTichXylanh
        {
            get { return _dungTichXylanh; }
            set
            {
                if (value <= 0)
                    throw new ArgumentException(
                        "Dung tich xilanh phai lon hon 0!");

                _dungTichXylanh = value;
            }
        }

        public XeMay(
            string maPT,
            string tenHang,
            int namSanXuat,
            decimal giaGoc,
            int dungTichXylanh)
            : base(maPT, tenHang, namSanXuat, giaGoc)
        {
            DungTichXylanh = dungTichXylanh;
        }

        public override decimal TinhGiaLanBanh()
        {
            if (DungTichXylanh < 175)
            {
                return GiaGoc
                    + GiaGoc * 0.02m;
            }
            else
            {
                return GiaGoc
                    + GiaGoc * 0.05m;
            }
        }

        public override string GetInfo()
        {
            return base.GetInfo()
                + " | Dung tich xilanh: "
                + DungTichXylanh + " cc";
        }
    }


    // Lop quan ly
    public class QuanLyPhuongTien
    {
        private List<PhuongTien> danhSach;

        public QuanLyPhuongTien()
        {
            danhSach = new List<PhuongTien>();
        }

        // Them phuong tien
        public void AddPhuongTien(PhuongTien pt)
        {
            danhSach.Add(pt);
        }

        // Hien thi tat ca
        public void DisplayAll()
        {
            foreach (PhuongTien pt in danhSach)
            {
                Console.WriteLine(pt.GetInfo());

                Console.WriteLine(
                    "Gia lan banh: "
                    + pt.TinhGiaLanBanh().ToString("N0")
                    + " VND");

                Console.WriteLine("--------------------------------------");
            }
        }

        // Tim phuong tien co gia lan banh cao nhat
        public PhuongTien FindMaxGiaLanBanh()
        {
            if (danhSach.Count == 0)
                return null;

            return danhSach
                .OrderByDescending(pt => pt.TinhGiaLanBanh())
                .First();
        }

        // Tim theo ten hang
        public List<PhuongTien> SearchByName(string keyword)
        {
            return danhSach
                .Where(pt => pt.TenHang.Contains(
                    keyword,
                    StringComparison.OrdinalIgnoreCase))
                .ToList();
        }
    }


    // Chuong trinh chinh
    class Program
    {
        static void Main(string[] args)
        {
            QuanLyPhuongTien ql = new QuanLyPhuongTien();

            OTo oto1 = new OTo(
                "OT001",
                "Toyota",
                2023,
                1000000000m,
                5,
                2.0);

            OTo oto2 = new OTo(
                "OT002",
                "Ford",
                2022,
                1200000000m,
                16,
                2.2);

            XeMay xeMay1 = new XeMay(
                "XM001",
                "Honda",
                2024,
                50000000m,
                150);

            XeMay xeMay2 = new XeMay(
                "XM002",
                "Yamaha",
                2023,
                70000000m,
                175);

            ql.AddPhuongTien(oto1);
            ql.AddPhuongTien(oto2);
            ql.AddPhuongTien(xeMay1);
            ql.AddPhuongTien(xeMay2);

            Console.WriteLine("===== DANH SACH PHUONG TIEN =====");
            ql.DisplayAll();

            Console.WriteLine();
            Console.WriteLine("===== PHUONG TIEN CO GIA LAN BANH CAO NHAT =====");

            PhuongTien max = ql.FindMaxGiaLanBanh();

            if (max != null)
            {
                Console.WriteLine(max.GetInfo());

                Console.WriteLine(
                    "Gia lan banh: "
                    + max.TinhGiaLanBanh().ToString("N0")
                    + " VND");
            }

            Console.WriteLine();
            Console.WriteLine("===== TIM KIEM HANG TOYOTA =====");

            List<PhuongTien> ketQua =
                ql.SearchByName("Toyota");

            foreach (PhuongTien pt in ketQua)
            {
                Console.WriteLine(pt.GetInfo());
            }

            Console.ReadKey();
        }
    }
}
<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/47a2a193-ffd3-4e9b-936b-784659ab051a" />
