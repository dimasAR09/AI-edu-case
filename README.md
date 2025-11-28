import React, { useState } from 'react';
import { 
  Brain, 
  Stethoscope, 
  Car, 
  Palette, 
  BadgeDollarSign, 
  GraduationCap, 
  Bot, 
  ArrowRight, 
  ExternalLink, 
  Cpu, 
  Layers,
  Sparkles,
  ChevronDown,
  ChevronUp,
  Sprout,
  Film,
  ShieldAlert
} from 'lucide-react';

const AI_Showcase_Edu = () => {
  const [activeTab, setActiveTab] = useState('all');
  const [expandedCard, setExpandedCard] = useState(null);

  // Data Studi Kasus AI
  const aiCaseStudies = [
    {
      id: 1,
      field: 'Kesehatan (HealthTech)',
      icon: <Stethoscope className="w-6 h-6" />,
      category: 'medical',
      appName: 'Google DermAssist',
      aiType: 'Computer Vision & Deep Learning',
      description: 'Alat berbasis AI yang membantu mendeteksi kondisi kulit, rambut, dan kuku.',
      details: 'Aplikasi ini menggunakan Convolutional Neural Networks (CNN) yang dilatih dengan jutaan gambar kondisi kulit. Pengguna cukup memotret area kulit yang bermasalah, dan AI akan membandingkannya dengan database medis untuk memberikan kemungkinan diagnosis awal.',
      impact: 'Meningkatkan akses diagnosis dermatologi bagi orang di daerah terpencil.',
      refLink: 'https://health.google/consumers/dermassist/'
    },
    {
      id: 2,
      field: 'Transportasi (Otomotif)',
      icon: <Car className="w-6 h-6" />,
      category: 'transport',
      appName: 'Tesla Autopilot (FSD)',
      aiType: 'Autonomous Robotics & Sensor Fusion',
      description: 'Sistem bantuan pengemudi canggih yang memungkinkan mobil mengemudi sendiri dalam kondisi tertentu.',
      details: 'Tesla menggunakan Neural Networks untuk memproses input dari 8 kamera secara real-time (HydraNet). AI ini melakukan deteksi objek, prediksi jalur, dan pengambilan keputusan navigasi tanpa campur tangan manusia secara penuh.',
      impact: 'Mengurangi kecelakaan akibat kelalaian manusia dan efisiensi lalu lintas.',
      refLink: 'https://www.tesla.com/autopilot'
    },
    {
      id: 3,
      field: 'Industri Kreatif',
      icon: <Palette className="w-6 h-6" />,
      category: 'creative',
      appName: 'Midjourney',
      aiType: 'Generative AI (Diffusion Models)',
      description: 'Platform AI yang mengubah teks (prompt) menjadi gambar artistik yang sangat realistis.',
      details: 'Menggunakan model difusi yang belajar "menghancurkan" dan "membangun kembali" gambar untuk memahami pola visual. Midjourney dapat memahami gaya seni, pencahayaan, dan komposisi kompleks dari perintah bahasa alami.',
      impact: 'Merevolusi cara desainer membuat konsep awal dan moodboard.',
      refLink: 'https://www.midjourney.com/'
    },
    {
      id: 4,
      field: 'Keuangan (Fintech)',
      icon: <BadgeDollarSign className="w-6 h-6" />,
      category: 'finance',
      appName: 'PayPal Fraud Protection',
      aiType: 'Predictive Analytics & Anomaly Detection',
      description: 'Sistem keamanan yang mendeteksi transaksi mencurigakan secara real-time.',
      details: 'Menggunakan Machine Learning Linear dan Deep Learning untuk menganalisis ribuan variabel data per detik. Jika pola transaksi menyimpang dari kebiasaan pengguna (anomali), sistem akan memblokir atau meminta verifikasi tambahan.',
      impact: 'Mencegah kerugian miliaran dolar akibat penipuan kartu kredit.',
      refLink: 'https://www.paypal.com/us/business/getting-started/fraud-protection'
    },
    {
      id: 5,
      field: 'Pendidikan',
      icon: <GraduationCap className="w-6 h-6" />,
      category: 'education',
      appName: 'Duolingo',
      aiType: 'NLP (Natural Language Processing) & Personalized Learning',
      description: 'Aplikasi belajar bahasa yang menyesuaikan kurikulum dengan kemampuan pengguna.',
      details: 'Menggunakan algoritma "Birdbrain" untuk memprediksi seberapa besar kemungkinan pengguna salah menjawab soal. AI menyesuaikan tingkat kesulitan secara dinamis agar pengguna tetap tertantang namun tidak frustrasi.',
      impact: 'Personalisasi pendidikan massal yang efektif dan gratis.',
      refLink: 'https://blog.duolingo.com/how-duolingo-uses-ai/'
    },
    {
      id: 6,
      field: 'Layanan Pelanggan',
      icon: <Bot className="w-6 h-6" />,
      category: 'service',
      appName: 'Intercom Fin / ChatGPT Enterprise',
      aiType: 'Large Language Models (LLM)',
      description: 'Chatbot cerdas yang dapat menyelesaikan masalah pelanggan tanpa agen manusia.',
      details: 'Berbeda dengan chatbot lama yang kaku, AI ini menggunakan model bahasa besar untuk memahami konteks percakapan, nuansa emosi, dan mencari jawaban spesifik dari dokumentasi perusahaan secara instan.',
      impact: 'Efisiensi operasional bisnis hingga 70% lebih cepat.',
      refLink: 'https://www.intercom.com/fin'
    },
    {
      id: 7,
      field: 'Pertanian (Agriculture)',
      icon: <Sprout className="w-6 h-6" />,
      category: 'agriculture',
      appName: 'John Deere See & Spray',
      aiType: 'Computer Vision & Robotics',
      description: 'Traktor pintar yang bisa membedakan tanaman dengan gulma secara real-time saat menyemprot pestisida.',
      details: 'Menggunakan kamera beresolusi tinggi dan machine learning yang dipasang di boom sprayer. Sistem mengidentifikasi setiap tanaman dalam hitungan milidetik dan hanya menyemprotkan herbisida pada gulma, bukan pada tanaman panen.',
      impact: 'Menghemat penggunaan bahan kimia hingga 77% dan menjaga lingkungan.',
      refLink: 'https://www.deere.com/en/sprayers/see-spray-ultimate/'
    },
    {
      id: 8,
      field: 'Hiburan (Streaming)',
      icon: <Film className="w-6 h-6" />,
      category: 'entertainment',
      appName: 'Netflix Recommendation Engine',
      aiType: 'Recommender Systems (Collaborative Filtering)',
      description: 'Sistem yang menyarankan film/serial berdasarkan kebiasaan menonton pengguna.',
      details: 'Menggunakan algoritma yang menganalisis riwayat tontonan, durasi menonton, dan preferensi pengguna lain yang serupa (collaborative filtering). AI ini memprediksi apa yang kemungkinan besar akan Anda nikmati selanjutnya.',
      impact: '80% konten yang ditonton di Netflix berasal dari rekomendasi algoritmanya.',
      refLink: 'https://research.netflix.com/research-area/recommendations'
    },
    {
      id: 9,
      field: 'Keamanan Siber',
      icon: <ShieldAlert className="w-6 h-6" />,
      category: 'security',
      appName: 'Darktrace',
      aiType: 'Unsupervised Machine Learning',
      description: 'Sistem "imun" digital yang mendeteksi serangan siber baru yang belum pernah dikenali sebelumnya.',
      details: 'Alih-alih menggunakan database virus lama, AI ini mempelajari pola "kehidupan normal" jaringan perusahaan. Jika ada aktivitas aneh (anomali) yang menyimpang dari pola normal tersebut, sistem langsung mengisolasi ancaman.',
      impact: 'Mendeteksi serangan ransomware dan phishing secara real-time sebelum menyebar.',
      refLink: 'https://darktrace.com/technology'
    }
  ];

  // List kategori untuk filter
  const categories = [
    { id: 'all', label: 'Semua Bidang' },
    { id: 'medical', label: 'Kesehatan' },
    { id: 'transport', label: 'Transportasi' },
    { id: 'creative', label: 'Kreatif' },
    { id: 'finance', label: 'Keuangan' },
    { id: 'agriculture', label: 'Pertanian' },
    { id: 'entertainment', label: 'Hiburan' },
    { id: 'security', label: 'Keamanan' }
  ];

  const filteredData = activeTab === 'all' 
    ? aiCaseStudies 
    : aiCaseStudies.filter(item => item.category === activeTab);

  const toggleExpand = (id) => {
    setExpandedCard(expandedCard === id ? null : id);
  };

  return (
    <div className="min-h-screen bg-slate-950 text-slate-100 font-sans selection:bg-indigo-500 selection:text-white">
      {/* Navbar */}
      <nav className="fixed w-full z-50 bg-slate-950/80 backdrop-blur-md border-b border-slate-800">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex items-center justify-between h-16">
            <div className="flex items-center space-x-2">
              <div className="bg-gradient-to-r from-indigo-500 to-purple-500 p-2 rounded-lg">
                <Brain className="w-6 h-6 text-white" />
              </div>
              <span className="text-xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-indigo-400 to-purple-400">
                AI EduCase
              </span>
            </div>
            <div className="hidden md:block">
              <span className="text-sm text-slate-400">Jawaban Tugas Data sains: Aplikasi AI & Tipenya</span>
            </div>
          </div>
        </div>
      </nav>

      {/* Hero Section */}
      <header className="pt-32 pb-16 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto text-center">
        <div className="inline-flex items-center px-4 py-2 rounded-full bg-indigo-900/30 border border-indigo-500/30 text-indigo-300 text-sm font-medium mb-6 animate-fade-in-up">
          <Sparkles className="w-4 h-4 mr-2" />
          Eksplorasi Teknologi Masa Depan
        </div>
        <h1 className="text-4xl md:text-6xl font-extrabold tracking-tight mb-6">
          Penerapan <span className="text-indigo-500">Artificial Intelligence</span><br />
          di Berbagai Sektor Industri
        </h1>
        <p className="max-w-2xl mx-auto text-lg text-slate-400 mb-10">
          Analisis mendalam mengenai bagaimana AI bekerja di dunia nyata, tipe teknologi yang digunakan, dan dampak signifikannya.
        </p>
        
        {/* Quick Concepts */}
        <div className="grid grid-cols-1 md:grid-cols-3 gap-4 max-w-4xl mx-auto mt-12 text-left">
          <div className="bg-slate-900/50 p-6 rounded-xl border border-slate-800 hover:border-indigo-500/50 transition-colors">
            <div className="bg-blue-500/10 w-10 h-10 rounded-lg flex items-center justify-center mb-4">
              <Cpu className="w-5 h-5 text-blue-400" />
            </div>
            <h3 className="font-semibold text-white mb-2">Narrow AI (Weak AI)</h3>
            <p className="text-sm text-slate-400">AI yang dirancang untuk satu tugas spesifik (contoh: Siri, Google Maps). Ini adalah tipe AI yang paling umum saat ini.</p>
          </div>
          <div className="bg-slate-900/50 p-6 rounded-xl border border-slate-800 hover:border-purple-500/50 transition-colors">
            <div className="bg-purple-500/10 w-10 h-10 rounded-lg flex items-center justify-center mb-4">
              <Layers className="w-5 h-5 text-purple-400" />
            </div>
            <h3 className="font-semibold text-white mb-2">Machine Learning</h3>
            <p className="text-sm text-slate-400">Cabang AI di mana mesin "belajar" dari data tanpa diprogram secara eksplisit untuk setiap aturan.</p>
          </div>
          <div className="bg-slate-900/50 p-6 rounded-xl border border-slate-800 hover:border-pink-500/50 transition-colors">
            <div className="bg-pink-500/10 w-10 h-10 rounded-lg flex items-center justify-center mb-4">
              <Brain className="w-5 h-5 text-pink-400" />
            </div>
            <h3 className="font-semibold text-white mb-2">Generative AI</h3>
            <p className="text-sm text-slate-400">Tipe AI baru yang bisa menciptakan konten baru (teks, gambar, audio) berdasarkan pola yang dipelajari.</p>
          </div>
        </div>
      </header>

      {/* Main Content Showcase */}
      <main className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        <div className="flex flex-col md:flex-row justify-between items-center mb-10">
          <h2 className="text-2xl font-bold text-white mb-4 md:mb-0">Katalog Aplikasi AI</h2>
          
          {/* Filter Tabs */}
          <div className="flex space-x-2 overflow-x-auto pb-2 md:pb-0 scrollbar-hide">
            {categories.map((tab) => (
              <button
                key={tab.id}
                onClick={() => setActiveTab(tab.id)}
                className={`px-4 py-2 rounded-full text-sm font-medium transition-all whitespace-nowrap ${
                  activeTab === tab.id 
                    ? 'bg-indigo-600 text-white shadow-lg shadow-indigo-500/30' 
                    : 'bg-slate-800 text-slate-400 hover:bg-slate-700'
                }`}
              >
                {tab.label}
              </button>
            ))}
          </div>
        </div>

        {/* Grid Cards */}
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {filteredData.map((item) => (
            <div 
              key={item.id}
              className={`group relative bg-slate-900 border border-slate-800 rounded-2xl overflow-hidden transition-all duration-300 hover:shadow-2xl hover:shadow-indigo-900/20 hover:-translate-y-1 ${expandedCard === item.id ? 'row-span-2' : ''}`}
            >
              {/* Card Header Gradient */}
              <div className="h-2 w-full bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 opacity-70 group-hover:opacity-100 transition-opacity" />
              
              <div className="p-6">
                <div className="flex justify-between items-start mb-4">
                  <div className="bg-slate-800 p-3 rounded-xl group-hover:bg-slate-700 transition-colors">
                    <div className="text-indigo-400">
                      {item.icon}
                    </div>
                  </div>
                  <span className="px-3 py-1 text-xs font-semibold rounded-full bg-slate-800 text-slate-300 border border-slate-700">
                    {item.field}
                  </span>
                </div>

                <h3 className="text-xl font-bold text-white mb-1">{item.appName}</h3>
                <p className="text-indigo-400 text-sm font-medium mb-4">{item.aiType}</p>
                <p className="text-slate-400 text-sm mb-6 leading-relaxed">
                  {item.description}
                </p>

                {/* Expandable Section */}
                <div className={`overflow-hidden transition-all duration-500 ${expandedCard === item.id ? 'max-h-96 opacity-100 mb-6' : 'max-h-0 opacity-0'}`}>
                  <div className="bg-slate-800/50 rounded-xl p-4 border border-slate-700/50">
                    <h4 className="text-sm font-bold text-white mb-2 flex items-center">
                      <Cpu className="w-3 h-3 mr-2 text-pink-400" /> Cara Kerja (Teknis):
                    </h4>
                    <p className="text-xs text-slate-300 mb-3 leading-relaxed border-b border-slate-700 pb-3">
                      {item.details}
                    </p>
                    <h4 className="text-sm font-bold text-white mb-1 flex items-center">
                      <Sparkles className="w-3 h-3 mr-2 text-yellow-400" /> Dampak Nyata:
                    </h4>
                    <p className="text-xs text-slate-300">
                      {item.impact}
                    </p>
                  </div>
                </div>

                <div className="flex items-center justify-between mt-auto pt-4 border-t border-slate-800">
                  <button 
                    onClick={() => toggleExpand(item.id)}
                    className="text-sm text-slate-300 hover:text-white flex items-center transition-colors"
                  >
                    {expandedCard === item.id ? 'Tutup Detail' : 'Lihat Detail'}
                    {expandedCard === item.id ? <ChevronUp className="w-4 h-4 ml-1" /> : <ChevronDown className="w-4 h-4 ml-1" />}
                  </button>
                  
                  <a 
                    href={item.refLink} 
                    target="_blank" 
                    rel="noopener noreferrer"
                    className="flex items-center text-sm font-medium text-indigo-400 hover:text-indigo-300 transition-colors"
                  >
                    Referensi <ExternalLink className="w-3 h-3 ml-1" />
                  </a>
                </div>
              </div>
            </div>
          ))}
        </div>
      </main>

      {/* Footer / References Section */}
      <footer className="bg-slate-900 border-t border-slate-800 py-12 mt-12">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
            <div>
              <h3 className="text-lg font-bold text-white mb-4">Tentang Jawaban Ini</h3>
              <p className="text-slate-400 text-sm leading-relaxed max-w-md">
                Dashboard ini dibuat sebagai jawaban tugas mengenai "Aplikasi AI dan Tipenya". 
                Informasi dikumpulkan dari studi kasus nyata perusahaan teknologi terkemuka untuk memberikan 
                konteks yang akurat dan edukatif.
              </p>
            </div>
            <div>
              <h3 className="text-lg font-bold text-white mb-4">Daftar Pustaka & Link Berguna</h3>
              <ul className="space-y-2 text-sm text-slate-400">
                <li>
                  <a href="https://www.ibm.com/topics/artificial-intelligence" className="hover:text-indigo-400 flex items-center">
                    <ArrowRight className="w-3 h-3 mr-2" /> IBM: What is Artificial Intelligence?
                  </a>
                </li>
                <li>
                  <a href="https://cloud.google.com/learn/what-is-artificial-intelligence" className="hover:text-indigo-400 flex items-center">
                    <ArrowRight className="w-3 h-3 mr-2" /> Google Cloud: AI Types & Applications
                  </a>
                </li>
                <li>
                  <a href="https://openai.com/research" className="hover:text-indigo-400 flex items-center">
                    <ArrowRight className="w-3 h-3 mr-2" /> OpenAI Research (Generative AI)
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div className="mt-8 pt-8 border-t border-slate-800 text-center text-slate-500 text-sm">
            © {new Date().getFullYear()} AI Case Study Project. Dibuat dengan React & Tailwind CSS.Dimas S1 Data Sains
          </div>
        </div>
      </footer>
    </div>
  );
};

export default AI_Showcase_Edu;# AI-edu-case
AI apps education 
