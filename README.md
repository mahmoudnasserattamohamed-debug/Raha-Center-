import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input"; import { Textarea } from "@/components/ui/textarea"; import { motion } from "framer-motion"; import { useState } from "react";

export default function CenterWebsite() { const [form, setForm] = useState({ name: "", phone: "", service: "", notes: "" });

const handleChange = (e) => { setForm({ ...form, [e.target.name]: e.target.value }); };

const whatsappNumber = "201063696177"; const whatsappLink = https://wa.me/${whatsappNumber}?text=${encodeURIComponent( اسم: ${form.name}\nخدمة: ${form.service}\nملاحظات: ${form.notes} )};

return ( <div className="min-h-screen bg-gray-50 text-gray-800"> {/* Header */} <header className="p-6 bg-white shadow-md flex justify-between items-center"> <h1 className="text-2xl font-bold text-blue-600">مركز راحة للرعاية الصحية</h1> <a href="#booking"> <Button>احجز الآن</Button> </a> </header>

{/* Hero */}
  <section className="text-center py-16 bg-blue-50">
    <motion.h2
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      className="text-3xl font-bold mb-4"
    >
      رعاية طبية وتمريض منزلي متكامل
    </motion.h2>
    <p className="text-lg text-gray-600">
      متابعة الأطفال – الحوامل – كبار السن – جلسات علاجية منزلية
    </p>
    <a href={whatsappLink} target="_blank">
      <Button className="mt-4">تواصل واتساب مباشر</Button>
    </a>
  </section>

  {/* Services */}
  <section className="p-8 grid md:grid-cols-3 gap-6">
    {[
      { title: "الرعاية المنزلية", desc: "تمريض ومتابعة 24 ساعة داخل المنزل" },
      { title: "متابعة الأطفال", desc: "متابعة الصفرة، التغذية، النمو" },
      { title: "رعاية الحوامل", desc: "ضغط – سكر – متابعة حمل كاملة" },
      { title: "جلسات بخار", desc: "ماكورت وأتروفينت بطريقة صحيحة" },
      { title: "رعاية كبار السن", desc: "متابعة مزمنة وتمريض منزلي" },
      { title: "تحاليل ومتابعة", desc: "متابعة طبية دقيقة للحالات" }
    ].map((s, i) => (
      <Card key={i}>
        <CardContent className="p-4">
          <h3 className="font-bold mb-2">{s.title}</h3>
          <p>{s.desc}</p>
        </CardContent>
      </Card>
    ))}
  </section>

  {/* Booking Form */}
  <section id="booking" className="p-8 bg-white">
    <h2 className="text-xl font-bold mb-4 text-center">حجز موعد</h2>
    <div className="max-w-xl mx-auto grid gap-3">
      <Input name="name" placeholder="الاسم" onChange={handleChange} />
      <Input name="phone" placeholder="رقم الهاتف" onChange={handleChange} />
      <Input name="service" placeholder="الخدمة المطلوبة" onChange={handleChange} />
      <Textarea name="notes" placeholder="ملاحظات" onChange={handleChange} />

      <a href={whatsappLink} target="_blank">
        <Button className="w-full">إرسال عبر واتساب</Button>
      </a>
    </div>
  </section>

  {/* Admin mock patient system */}
  <section className="p-8 bg-gray-100">
    <h2 className="text-xl font-bold mb-4">نظام متابعة الحالات (إداري)</h2>
    <div className="grid md:grid-cols-2 gap-4">
      <Card>
        <CardContent className="p-4">
          <h3 className="font-bold">حالة #1</h3>
          <p>طفل – صفرة متوسطة – متابعة بعد 48 ساعة</p>
        </CardContent>
      </Card>

      <Card>
        <CardContent className="p-4">
          <h3 className="font-bold">حالة #2</h3>
          <p>حامل – ضغط مرتفع – متابعة يومية</p>
        </CardContent>
      </Card>
    </div>
  </section>

  {/* Footer */}
  <footer className="p-6 text-center text-sm text-gray-500">
    © 2026 مركز راحة للرعاية الصحية | جميع الحقوق محفوظة
  </footer>
</div>

); }
