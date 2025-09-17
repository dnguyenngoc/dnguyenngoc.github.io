---
title: "Welcome to My Digital Space"
description: "Senior Data Engineer crafting intelligent solutions at the intersection of AI, big data, and scalable systems"
---

## Hello, I'm Duy! 👋

Welcome to my corner of the internet! I'm a **Senior Data Engineer** at [VieON](https://vieon.vn/), where I architect and build robust data infrastructure that powers intelligent decision-making. With a passion for transforming raw data into actionable insights, I specialize in creating scalable systems that handle massive datasets with precision and efficiency.

### My Journey in Data & AI

I'm deeply fascinated by the transformative power of artificial intelligence and machine learning. My work revolves around building the foundational infrastructure that enables organizations to harness the full potential of their data assets. From real-time streaming analytics to distributed machine learning pipelines, I'm constantly exploring innovative approaches to solve complex data challenges.

<div class="profile-section">
    <div class="profile-content">
        <div class="interests">
            <h3>Core Expertise</h3>
            <ul>
                <li><strong>Data Engineering</strong> - Building scalable ETL pipelines and data warehouses</li>
                <li><strong>Machine Learning</strong> - Developing and deploying ML models in production</li>
                <li><strong>Cloud Infrastructure</strong> - Apache Spark, Kubernetes, and distributed computing</li>
                <li><strong>Real-time Analytics</strong> - Streaming data processing and real-time insights</li>
            </ul>
        </div>
        <div class="profile-image">
            <img src='/dog.gif' alt='Profile animation' class="profile-gif"/>
        </div>
    </div>
</div>



## Professional Profile

<embed-pdf url="./pdf-cv/duynguyen-cv.pdf" hidePaginator="true" />

**Download my comprehensive CV**: [PDF Version](/pdf-cv/duynguyen-cv.pdf)

## Let's Connect

I'm always excited to connect with fellow data enthusiasts, potential collaborators, and industry professionals. Whether you're interested in discussing data engineering challenges, exploring new technologies, or simply want to share insights about the evolving landscape of AI and big data, I'd love to hear from you.

- [duynguyenngoc@hotmail.com](mailto:duynguyenngoc@hotmail.com)
- [LinkedIn](https://www.linkedin.com/in/dnguyenngoc/)
- [GitHub](https://github.com/dnguyenngoc/)

## 🎮 Fun & Games

Take a break from coding and challenge yourself with our collection of interactive games!

<div style="background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%); border-radius: 12px; padding: 20px; margin: 15px 0; text-align: center; box-shadow: 0 4px 15px rgba(255, 154, 158, 0.3);">
  <h4 style="margin: 0 0 10px 0; color: white; font-size: 1.2em;">🎯 Brain Training Games</h4>
  <p style="margin: 0 0 15px 0; color: rgba(255,255,255,0.9); font-size: 0.95em;">Sharpen your mind with classic puzzle and strategy games</p>
  <div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin: 15px 0;">
    <span style="background: rgba(255,255,255,0.2); padding: 8px 12px; border-radius: 15px; color: white; font-size: 0.8em;">⭕ Tic-Tac-Toe vs AI</span>
    <span style="background: rgba(255,255,255,0.2); padding: 8px 12px; border-radius: 15px; color: white; font-size: 0.8em;">🔢 2048 Puzzle</span>
  </div>
  <a href="/game/" style="display: inline-block; background: white; color: #ff9a9e; padding: 12px 24px; border-radius: 25px; text-decoration: none; font-weight: bold; transition: all 0.3s ease; box-shadow: 0 2px 8px rgba(0,0,0,0.2);">
    🎮 Play Now
  </a>
  <p style="margin: 10px 0 0 0; color: rgba(255,255,255,0.8); font-size: 0.8em;">Perfect for breaks between coding sessions!</p>
</div>

## ☕ Support My Work

If you find my content helpful and would like to support my work, you can:

### 🛍️ Shop My Recommendations
<div style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); border-radius: 12px; padding: 20px; margin: 15px 0; text-align: center; box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);">
  <h4 style="margin: 0 0 10px 0; color: white; font-size: 1.2em;">🛍️ Discover Amazing Products</h4>
  <p style="margin: 0 0 15px 0; color: rgba(255,255,255,0.9); font-size: 0.95em;">Products I personally use and recommend</p>
  <a href="/shop/" class="shop-cta-button" style="display: inline-block; background: white; color: #667eea; padding: 12px 24px; border-radius: 25px; text-decoration: none; font-weight: bold; transition: all 0.3s ease; box-shadow: 0 2px 8px rgba(0,0,0,0.2);">
    🛒 Visit My Shop
  </a>
  <p style="margin: 10px 0 0 0; color: rgba(255,255,255,0.8); font-size: 0.8em;">Every purchase supports my content creation!</p>
</div>

### 💰 Direct Donation
You can also donate directly via TRC20:

**TRC20 Address:** `TM8XN2F8pAf4DPd7aPk7LSV5MneUrfHKuy`

<div id="donate-box" style="background-color: #f8f9fa; border: 1px solid #e9ecef; border-radius: 8px; padding: 15px; margin: 20px 0; text-align: center; cursor: pointer; transition: all 0.3s ease;" title="Click to copy">
  <p id="address-text" style="margin: 0; font-family: monospace; font-size: 0.9em; word-break: break-all; color: #495057;">
    TM8XN2F8pAf4DPd7aPk7LSV5MneUrfHKuy
  </p>
  <p id="copy-text" style="margin: 5px 0 0 0; font-size: 0.8em; color: #6c757d;">
    Click to copy address
  </p>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const donateBox = document.getElementById('donate-box');
  const addressText = document.getElementById('address-text');
  const copyText = document.getElementById('copy-text');
  const originalText = copyText.textContent;
  
  donateBox.addEventListener('click', function() {
    const textToCopy = 'TM8XN2F8pAf4DPd7aPk7LSV5MneUrfHKuy';
    
    // Try modern clipboard API first
    if (navigator.clipboard && window.isSecureContext) {
      navigator.clipboard.writeText(textToCopy).then(function() {
        showSuccess();
      }).catch(function() {
        fallbackCopy();
      });
    } else {
      fallbackCopy();
    }
  });
  
  function showSuccess() {
    // Change text
    copyText.innerHTML = '✅ Copied to clipboard!';
    
    // Visual feedback
    donateBox.style.backgroundColor = '#d4edda';
    donateBox.style.borderColor = '#28a745';
    donateBox.style.borderWidth = '2px';
    donateBox.style.transform = 'scale(1.05)';
    donateBox.style.boxShadow = '0 4px 12px rgba(40, 167, 69, 0.4)';
    
    // Address text effect
    addressText.style.color = '#28a745';
    addressText.style.fontWeight = 'bold';
    
    // Show toast notification
    showToast('🎉 Address copied successfully!');
    
    // Reset after 2 seconds
    setTimeout(function() {
      copyText.textContent = originalText;
      donateBox.style.backgroundColor = '#f8f9fa';
      donateBox.style.borderColor = '#e9ecef';
      donateBox.style.borderWidth = '1px';
      donateBox.style.transform = 'scale(1)';
      donateBox.style.boxShadow = 'none';
      addressText.style.color = '#495057';
      addressText.style.fontWeight = 'normal';
    }, 2000);
  }
  
  function fallbackCopy() {
    // Fallback for older browsers
    const textArea = document.createElement('textarea');
    textArea.value = 'TM8XN2F8pAf4DPd7aPk7LSV5MneUrfHKuy';
    textArea.style.position = 'fixed';
    textArea.style.left = '-999999px';
    textArea.style.top = '-999999px';
    document.body.appendChild(textArea);
    textArea.focus();
    textArea.select();
    
    try {
      document.execCommand('copy');
      showSuccess();
    } catch (err) {
      copyText.innerHTML = '❌ Copy failed - please select and copy manually';
      donateBox.style.backgroundColor = '#f8d7da';
      donateBox.style.borderColor = '#dc3545';
    }
    
    document.body.removeChild(textArea);
  }
  
  function showToast(message) {
    const toast = document.createElement('div');
    toast.innerHTML = message;
    toast.style.cssText = `
      position: fixed;
      top: 20px;
      right: 20px;
      background: #28a745;
      color: white;
      padding: 12px 20px;
      border-radius: 6px;
      font-weight: bold;
      z-index: 10000;
      box-shadow: 0 4px 12px rgba(0,0,0,0.3);
      animation: slideInRight 0.3s ease;
    `;
    
    // Add animation
    const style = document.createElement('style');
    style.textContent = `
      @keyframes slideInRight {
        from {
          transform: translateX(100%);
          opacity: 0;
        }
        to {
          transform: translateX(0);
          opacity: 1;
        }
      }
    `;
    document.head.appendChild(style);
    
    document.body.appendChild(toast);
    
    setTimeout(function() {
      toast.remove();
      style.remove();
    }, 3000);
  }
});
</script>

---

## Featured Work & Insights

### 🚀 Engineering Projects

- **[Spark Operator on Kubernetes](/de/spark-operator-on-k8s)** - Orchestrating distributed computing for big data workloads
- **[ML Models in Production](https://github.com/apot-group/ml-models-in-production)** - End-to-end machine learning model serving infrastructure
- **[Real-time Analytics Platform](https://github.com/apot-group/real-time-analytic)** - High-performance streaming data processing pipeline

### 📚 Technical Articles & Tutorials

- **[Real-time Analytics: Airflow + Kafka + Druid + Superset](/posts/real-time-analytics-airflow-kafka-druid-superset)** - A comprehensive guide to building modern streaming analytics architecture
- **[Cats vs Dogs Classification using CNN Keras](/posts/cats-vs-dogs-classification-using-cnn-keras)** - Deep learning computer vision from concept to deployment
- **[Spark Distributed ML with Pandas UDFs](/posts/spark-distributed-ml-model-with-pandas-udfs)** - Scaling machine learning workflows across distributed systems
- **[Serving ML Models with FastAPI and Celery](/posts/serving-ml-models-in-production-with-fastapi-and-celery)** - Production-ready machine learning model serving with modern Python frameworks

