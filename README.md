Nền tảng thương mại điện tử chuyên biệt cho thiết bị di động IMEX
import Link from "next/link";

export default function Home() {
  return (
    <>
      {/* Hero Section */}
      <section className="hero-bg min-h-screen flex items-center pt-20">
        <div className="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
          <div className="space-y-8">
            <div className="inline-flex items-center gap-2 bg-white/70 backdrop-blur px-5 py-2 rounded-full text-sm font-medium">
              ✨ Nền tảng chuyên biệt thiết bị di động
            </div>

            <h1 className="text-6xl md:text-7xl font-bold tracking-tighter leading-none">
              Mua sắm thông minh.<br />
              So sánh dễ dàng.<br />
              <span className="text-[#0891b2]">Bảo hành điện tử</span>.
            </h1>

            <p className="text-xl text-slate-600 max-w-lg">
              IMEX - Nền tảng thương mại điện tử chuyên sâu cho điện thoại, máy tính bảng và phụ kiện công nghệ tại Việt Nam.
            </p>

            <div className="flex flex-wrap gap-4">
              <Link 
                href="/products" 
                className="bg-slate-900 hover:bg-black text-white px-10 py-4 rounded-2xl font-semibold text-lg transition"
              >
                Khám phá sản phẩm
              </Link>
              <Link 
                href="/compare" 
                className="border-2 border-slate-800 hover:bg-slate-100 px-10 py-4 rounded-2xl font-semibold text-lg transition"
              >
                So sánh ngay
              </Link>
            </div>
          </div>

          <div className="relative hidden md:block">
            <div className="bg-white rounded-3xl shadow-2xl p-4">
              <img 
                src="https://picsum.photos/id/1015/700/520" 
                alt="Điện thoại cao cấp" 
                className="rounded-2xl shadow-lg"
              />
            </div>
          </div>
        </div>
      </section>

      {/* Tính năng chính */}
      <section className="py-24 bg-white">
        <div className="max-w-7xl mx-auto px-6">
          <h2 className="text-4xl font-bold text-center mb-16">Tính năng nổi bật của IMEX</h2>
          <div className="grid md:grid-cols-3 gap-8">
            {[
              { title: "So sánh thiết bị", desc: "Đối chiếu thông số kỹ thuật chi tiết giữa nhiều sản phẩm" },
              { title: "Bảo hành điện tử", desc: "Lưu trữ và tra cứu thông tin bảo hành dễ dàng" },
              { title: "Cộng đồng công nghệ", desc: "Chia sẻ đánh giá và kinh nghiệm sử dụng" },
            ].map((item, i) => (
              <div key={i} className="bg-slate-50 p-10 rounded-3xl hover:shadow-xl transition">
                <div className="w-14 h-14 bg-[#9BF6FF] rounded-2xl mb-6" />
                <h3 className="text-2xl font-semibold mb-3">{item.title}</h3>
                <p className="text-slate-600">{item.desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>
    </>
  );
}
