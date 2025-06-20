"use client"

import type React from "react"
import { useState, useRef, useEffect } from "react"
import { motion, useAnimation } from "framer-motion"
import emailjs from "@emailjs/browser"

const RobotContactForm = () => {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
    message: "",
  })
  const [isSending, setIsSending] = useState(false)
  const [success, setSuccess] = useState<boolean | null>(null)

  const robotEyeControls = useAnimation()
  const robotDisplayRef = useRef<HTMLSpanElement>(null)
  const formRef = useRef<HTMLFormElement>(null)

  const handleChange = (e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement>) => {
    setFormData({ ...formData, [e.target.name]: e.target.value })
  }

  const sendEmail = async (e: React.FormEvent) => {
    e.preventDefault()
    setIsSending(true)
    setSuccess(null)

    // Animate robot response
    robotEyeControls.start({
      scaleY: [1, 0.3, 1, 0.3, 1],
      transition: { duration: 1, times: [0, 0.2, 0.4, 0.6, 1] },
    })

    // Update robot display
    if (robotDisplayRef.current) {
      robotDisplayRef.current.textContent = "TRANSMITTING..."
    }

    try {
      // Get environment variables (these should be set in your .env file)
      const serviceID = process.env.NEXT_PUBLIC_SERVICE_ID!
      const templateID = process.env.NEXT_PUBLIC_TEMPLATE_ID!
      const publicKey = process.env.NEXT_PUBLIC_PUBLIC_KEY!

      const templateParams = {
        from_name: formData.name,
        from_email: formData.email,
        to_email: "khoerulfajri1999@gmail.com",
        message: formData.message,
        reply_to: formData.email,
      }

      const response = await emailjs.send(serviceID, templateID, templateParams, publicKey)

      console.log("SUCCESS!", response.status, response.text)
      setSuccess(true)
      setFormData({ name: "", email: "", message: "" }) // Reset form

      if (robotDisplayRef.current) {
        robotDisplayRef.current.textContent = "MESSAGE_SENT!"
      }
    } catch (err) {
      console.log("FAILED...", err)
      setSuccess(false)

      if (robotDisplayRef.current) {
        robotDisplayRef.current.textContent = "TRANSMISSION_FAILED"
      }
    } finally {
      setIsSending(false)

      // Reset robot display after 3 seconds
      setTimeout(() => {
        if (robotDisplayRef.current) {
          robotDisplayRef.current.textContent = "READY_TO_RECEIVE"
        }
      }, 3000)
    }
  }

  useEffect(() => {
    // Reset success message after 5 seconds
    if (success !== null) {
      const timer = setTimeout(() => setSuccess(null), 5000)
      return () => clearTimeout(timer)
    }
  }, [success])

  return (
    <section className="relative py-20 bg-gradient-to-tl from-[#030415] via-[#1E0B38] to-[#030415] overflow-hidden min-h-screen">
      {/* Animated Background Grid */}
      <div className="absolute inset-0 bg-[linear-gradient(rgba(120,119,198,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(120,119,198,0.1)_1px,transparent_1px)] bg-[size:50px_50px]">
        <motion.div
          className="w-full h-full"
          animate={{
            backgroundPosition: ["0px 0px", "50px 50px"],
          }}
          transition={{
            duration: 20,
            repeat: Number.POSITIVE_INFINITY,
            ease: "linear",
          }}
        />
      </div>

      {/* Floating Circuit Elements */}
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        <motion.div
          className="absolute top-20 left-10 w-32 h-32 opacity-30"
          animate={{ rotate: 360 }}
          transition={{ duration: 8, repeat: Number.POSITIVE_INFINITY, ease: "linear" }}
        >
          <svg viewBox="0 0 100 100" className="w-full h-full text-cyan-400">
            <circle cx="20" cy="20" r="3" fill="currentColor" />
            <circle cx="80" cy="20" r="3" fill="currentColor" />
            <circle cx="50" cy="50" r="5" fill="currentColor" />
            <circle cx="20" cy="80" r="3" fill="currentColor" />
            <circle cx="80" cy="80" r="3" fill="currentColor" />
            <path d="M20 20 L50 50 L80 20 M20 80 L50 50 L80 80" stroke="currentColor" strokeWidth="1" fill="none" />
          </svg>
        </motion.div>

        <motion.div
          className="absolute top-40 right-20 w-24 h-24 opacity-40"
          animate={{ rotate: -360 }}
          transition={{ duration: 6, repeat: Number.POSITIVE_INFINITY, ease: "linear" }}
        >
          <svg viewBox="0 0 100 100" className="w-full h-full text-green-400">
            <rect x="10" y="10" width="80" height="80" fill="none" stroke="currentColor" strokeWidth="2" />
            <circle cx="30" cy="30" r="4" fill="currentColor" />
            <circle cx="70" cy="30" r="4" fill="currentColor" />
            <circle cx="50" cy="70" r="6" fill="currentColor" />
            <path d="M30 30 L70 30 L50 70 Z" stroke="currentColor" strokeWidth="1" fill="none" />
          </svg>
        </motion.div>
      </div>

      {/* Glowing Orbs */}
      <motion.div
        className="absolute top-1/4 left-1/6 w-4 h-4 bg-cyan-400 rounded-full blur-sm"
        animate={{
          scale: [1, 1.5, 1],
          opacity: [0.6, 0.8, 0.6],
        }}
        transition={{
          duration: 2,
          repeat: Number.POSITIVE_INFINITY,
          ease: "easeInOut",
        }}
      />

      <div className="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        {/* Section Header */}
        <motion.div
          className="text-center mb-16"
          initial={{ opacity: 0, y: 50 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1 }}
        >
          {/* Robot Head Icon */}
          <motion.div
            className="mx-auto mb-8 w-24 h-24 relative"
            initial={{ scale: 0, rotate: 180 }}
            animate={{ scale: 1, rotate: 0 }}
            transition={{ duration: 1, type: "spring", stiffness: 100 }}
          >
            <div className="w-full h-full bg-gradient-to-br from-cyan-400 to-blue-500 rounded-lg relative overflow-hidden shadow-2xl">
              <div className="absolute inset-2 bg-gray-900 rounded-md flex items-center justify-center">
                <div className="flex space-x-3">
                  <motion.div
                    className="w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"
                    animate={{
                      scaleY: [1, 0.1, 1],
                    }}
                    transition={{
                      duration: 0.1,
                      repeat: Number.POSITIVE_INFINITY,
                      repeatDelay: 3,
                    }}
                  />
                  <motion.div
                    className="w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"
                    animate={{
                      scaleY: [1, 0.1, 1],
                    }}
                    transition={{
                      duration: 0.1,
                      repeat: Number.POSITIVE_INFINITY,
                      repeatDelay: 3,
                      delay: 0.05,
                    }}
                  />
                </div>
                <div className="absolute bottom-2 left-1/2 transform -translate-x-1/2 w-4 h-1 bg-cyan-400 rounded-full opacity-60" />
              </div>
              <motion.div
                className="absolute -top-2 left-1/2 transform -translate-x-1/2 w-1 h-4 bg-cyan-400 rounded-full"
                animate={{
                  scale: [1, 1.2, 1],
                  opacity: [0.8, 1, 0.8],
                }}
                transition={{
                  duration: 1.5,
                  repeat: Number.POSITIVE_INFINITY,
                  ease: "easeInOut",
                }}
              />
              <motion.div
                className="absolute -top-3 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"
                animate={{
                  scale: [1, 1.2, 1],
                  opacity: [0.8, 1, 0.8],
                }}
                transition={{
                  duration: 1.5,
                  repeat: Number.POSITIVE_INFINITY,
                  ease: "easeInOut",
                }}
              />
            </div>
          </motion.div>

          <motion.h2
            className="text-5xl sm:text-6xl font-bold mb-6"
            initial={{ opacity: 0, y: 30 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8, delay: 0.2 }}
          >
            <span className="bg-gradient-to-r from-cyan-400 via-blue-400 to-green-400 bg-clip-text text-transparent">
              SEND MESSAGE
            </span>
          </motion.h2>

          <motion.p
            className="text-xl text-gray-300 mb-4"
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.6, delay: 0.4 }}
          >
            <span className="text-cyan-400 font-mono">[SYSTEM READY]</span> Let's work together!
          </motion.p>

          <motion.div
            className="flex items-center justify-center space-x-2"
            initial={{ opacity: 0, scale: 0 }}
            animate={{ opacity: 1, scale: 1 }}
            transition={{ duration: 0.6, delay: 0.6, type: "spring" }}
          >
            <motion.div
              className="w-2 h-2 bg-green-400 rounded-full"
              animate={{ opacity: [1, 0.3, 1] }}
              transition={{ duration: 1, repeat: Number.POSITIVE_INFINITY }}
            />
            <span className="text-green-400 font-mono text-sm">CONNECTION_ACTIVE</span>
          </motion.div>
        </motion.div>

        {/* Main Content Grid */}
        <div className="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          {/* Left Side - Robot Illustration */}
          <motion.div
            className="relative"
            initial={{ opacity: 0, x: -100 }}
            animate={{ opacity: 1, x: 0 }}
            transition={{ duration: 1.2, delay: 0.8 }}
          >
            <div className="w-80 h-96 mx-auto relative">
              {/* Robot Torso */}
              <motion.div
                className="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-48 h-64 bg-gradient-to-b from-gray-700 to-gray-800 rounded-t-3xl border-2 border-cyan-400/30 shadow-2xl"
                initial={{ scale: 0.8, opacity: 0 }}
                animate={{ scale: 1, opacity: 1 }}
                transition={{ duration: 1, delay: 1.2 }}
              >
                {/* Chest Panel */}
                <div className="absolute top-8 left-1/2 transform -translate-x-1/2 w-32 h-20 bg-gray-900 rounded-lg border border-cyan-400/50">
                  {/* Status Lights */}
                  <div className="flex justify-center space-x-2 mt-3">
                    <motion.div
                      className="w-2 h-2 bg-green-400 rounded-full"
                      animate={{
                        scale: [1, 1.3, 1],
                        opacity: [0.7, 1, 0.7],
                      }}
                      transition={{
                        duration: 0.5,
                        repeat: Number.POSITIVE_INFINITY,
                        repeatType: "reverse",
                      }}
                    />
                    <motion.div
                      className="w-2 h-2 bg-blue-400 rounded-full"
                      animate={{
                        scale: [1, 1.3, 1],
                        opacity: [0.7, 1, 0.7],
                      }}
                      transition={{
                        duration: 0.5,
                        repeat: Number.POSITIVE_INFINITY,
                        repeatType: "reverse",
                        delay: 0.2,
                      }}
                    />
                    <motion.div
                      className="w-2 h-2 bg-cyan-400 rounded-full"
                      animate={{
                        scale: [1, 1.3, 1],
                        opacity: [0.7, 1, 0.7],
                      }}
                      transition={{
                        duration: 0.5,
                        repeat: Number.POSITIVE_INFINITY,
                        repeatType: "reverse",
                        delay: 0.4,
                      }}
                    />
                  </div>
                  {/* Display Screen */}
                  <div className="mt-2 mx-2 h-8 bg-black rounded border border-cyan-400/30 flex items-center justify-center">
                    <span ref={robotDisplayRef} className="text-cyan-400 font-mono text-xs">
                      READY_TO_RECEIVE
                    </span>
                  </div>
                </div>

                {/* Arms */}
                <motion.div
                  className="absolute top-16 -left-8 w-6 h-32 bg-gradient-to-b from-gray-600 to-gray-700 rounded-full border border-cyan-400/30"
                  animate={{ rotate: [0, 5, 0] }}
                  transition={{ duration: 4, repeat: Number.POSITIVE_INFINITY, repeatType: "reverse" }}
                />
                <motion.div
                  className="absolute top-16 -right-8 w-6 h-32 bg-gradient-to-b from-gray-600 to-gray-700 rounded-full border border-cyan-400/30"
                  animate={{ rotate: [0, -5, 0] }}
                  transition={{ duration: 4, repeat: Number.POSITIVE_INFINITY, repeatType: "reverse" }}
                />

                {/* Hands */}
                <div className="absolute top-44 -left-10 w-8 h-8 bg-gray-600 rounded-full border border-cyan-400/30" />
                <div className="absolute top-44 -right-10 w-8 h-8 bg-gray-600 rounded-full border border-cyan-400/30" />
              </motion.div>

              {/* Robot Head */}
              <motion.div
                className="absolute top-0 left-1/2 transform -translate-x-1/2 w-32 h-32 bg-gradient-to-br from-gray-600 to-gray-800 rounded-2xl border-2 border-cyan-400/50 shadow-2xl"
                initial={{ y: -50, opacity: 0 }}
                animate={{ y: 0, opacity: 1 }}
                transition={{ duration: 0.8, delay: 1.4, type: "spring" }}
              >
                {/* Face Screen */}
                <div className="absolute inset-4 bg-black rounded-lg border border-cyan-400/30 flex flex-col items-center justify-center">
                  {/* Main Eyes */}
                  <div className="flex space-x-4 mb-2">
                    <motion.div
                      className="w-4 h-4 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"
                      animate={robotEyeControls}
                    />
                    <motion.div
                      className="w-4 h-4 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"
                      animate={robotEyeControls}
                    />
                  </div>
                  {/* Expression Line */}
                  <div className="w-8 h-0.5 bg-cyan-400 rounded-full" />
                </div>

                {/* Head Antenna */}
                <div className="absolute -top-4 left-1/2 transform -translate-x-1/2 w-2 h-6 bg-cyan-400 rounded-full" />
                <motion.div
                  className="absolute -top-6 left-1/2 transform -translate-x-1/2 w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"
                  animate={{
                    scale: [1, 1.2, 1],
                    opacity: [0.8, 1, 0.8],
                  }}
                  transition={{
                    duration: 1.5,
                    repeat: Number.POSITIVE_INFINITY,
                    ease: "easeInOut",
                  }}
                />
              </motion.div>

              {/* Holographic Effect */}
              <motion.div
                className="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-64 h-4 bg-gradient-to-r from-transparent via-cyan-400/20 to-transparent rounded-full blur-sm"
                animate={{
                  scaleX: [1, 1.2, 1],
                  opacity: [0.2, 0.4, 0.2],
                }}
                transition={{
                  duration: 2,
                  repeat: Number.POSITIVE_INFINITY,
                  ease: "easeInOut",
                }}
              />
            </div>
          </motion.div>

          {/* Right Side - Message Form */}
          <motion.div
            initial={{ opacity: 0, x: 100 }}
            animate={{ opacity: 1, x: 0 }}
            transition={{ duration: 1.2, delay: 1 }}
          >
            <div className="bg-gray-900/80 backdrop-blur-md rounded-2xl p-8 border border-cyan-400/30 shadow-2xl relative overflow-hidden">
              {/* Form Header */}
              <div className="flex items-center justify-between mb-6">
                <div className="flex items-center space-x-3">
                  <motion.div
                    className="w-3 h-3 bg-green-400 rounded-full"
                    animate={{ opacity: [1, 0.3, 1] }}
                    transition={{ duration: 1, repeat: Number.POSITIVE_INFINITY }}
                  />
                  <span className="text-cyan-400 font-mono text-sm">COMMUNICATION_INTERFACE</span>
                </div>
                <div className="text-gray-400 font-mono text-xs">v1.0.0</div>
              </div>

              {/* Scanning Line Effect */}
              <motion.div
                className="absolute left-0 w-full h-0.5 bg-gradient-to-r from-transparent via-cyan-400 to-transparent opacity-60"
                animate={{
                  top: ["0%", "100%"],
                }}
                transition={{
                  duration: 3,
                  repeat: Number.POSITIVE_INFINITY,
                  ease: "easeInOut",
                }}
              />

              <form ref={formRef} onSubmit={sendEmail} className="space-y-6">
                {/* Name Input */}
                <motion.div
                  initial={{ opacity: 0, y: 30 }}
                  animate={{ opacity: 1, y: 0 }}
                  transition={{ duration: 0.6, delay: 1.2 }}
                >
                  <label className="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                    <span className="text-gray-500">[01]</span> NAME
                  </label>
                  <div className="relative">
                    <input
                      name="name"
                      value={formData.name}
                      onChange={handleChange}
                      type="text"
                      required
                      className="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 font-mono focus:scale-[1.02]"
                      placeholder="Enter your name..."
                    />
                    <div className="absolute right-3 top-1/2 transform -translate-y-1/2 w-2 h-2 bg-cyan-400 rounded-full opacity-60" />
                  </div>
                </motion.div>

                {/* Email Input */}
                <motion.div
                  initial={{ opacity: 0, y: 30 }}
                  animate={{ opacity: 1, y: 0 }}
                  transition={{ duration: 0.6, delay: 1.3 }}
                >
                  <label className="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                    <span className="text-gray-500">[02]</span> EMAIL
                  </label>
                  <div className="relative">
                    <input
                      name="email"
                      value={formData.email}
                      onChange={handleChange}
                      type="email"
                      required
                      className="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 font-mono focus:scale-[1.02]"
                      placeholder="Enter your email..."
                    />
                    <div className="absolute right-3 top-1/2 transform -translate-y-1/2 w-2 h-2 bg-green-400 rounded-full opacity-60" />
                  </div>
                </motion.div>

                {/* Message Input */}
                <motion.div
                  initial={{ opacity: 0, y: 30 }}
                  animate={{ opacity: 1, y: 0 }}
                  transition={{ duration: 0.6, delay: 1.4 }}
                >
                  <label className="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                    <span className="text-gray-500">[03]</span> MESSAGE
                  </label>
                  <div className="relative">
                    <textarea
                      name="message"
                      value={formData.message}
                      onChange={handleChange}
                      required
                      rows={5}
                      className="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 resize-none font-mono focus:scale-[1.02]"
                      placeholder="Enter your message..."
                    />
                    <div className="absolute right-3 bottom-3 w-2 h-2 bg-blue-400 rounded-full opacity-60" />
                  </div>
                </motion.div>

                {/* Submit Button */}
                <motion.div
                  initial={{ opacity: 0, y: 30 }}
                  animate={{ opacity: 1, y: 0 }}
                  transition={{ duration: 0.6, delay: 1.5 }}
                >
                  <motion.button
                    type="submit"
                    disabled={isSending}
                    className="w-full bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 disabled:opacity-50 text-white font-bold py-4 px-8 rounded-lg text-lg transition-all duration-300 shadow-lg hover:shadow-cyan-400/25 font-mono uppercase tracking-wider relative overflow-hidden"
                    whileHover={{ scale: 1.05 }}
                    whileTap={{ scale: 0.95 }}
                  >
                    {isSending ? (
                      <span className="flex items-center justify-center">
                        <motion.div
                          className="w-5 h-5 mr-2 border-2 border-white border-t-transparent rounded-full"
                          animate={{ rotate: 360 }}
                          transition={{ duration: 1, repeat: Number.POSITIVE_INFINITY, ease: "linear" }}
                        />
                        TRANSMITTING...
                      </span>
                    ) : (
                      "SEND MESSAGE"
                    )}
                  </motion.button>
                </motion.div>

                {/* Success/Error Messages */}
                {success === true && (
                  <motion.div
                    initial={{ opacity: 0, y: 20 }}
                    animate={{ opacity: 1, y: 0 }}
                    className="text-green-400 text-center font-mono text-sm bg-green-400/10 border border-green-400/30 rounded-lg p-3"
                  >
                    [SUCCESS] Message transmitted successfully!
                  </motion.div>
                )}
                {success === false && (
                  <motion.div
                    initial={{ opacity: 0, y: 20 }}
                    animate={{ opacity: 1, y: 0 }}
                    className="text-red-400 text-center font-mono text-sm bg-red-400/10 border border-red-400/30 rounded-lg p-3"
                  >
                    [ERROR] Failed to send message. Please try again.
                  </motion.div>
                )}
              </form>

              {/* Status Bar */}
              <motion.div
                className="mt-6 flex items-center justify-between text-xs font-mono"
                initial={{ opacity: 0 }}
                animate={{ opacity: 1 }}
                transition={{ duration: 0.6, delay: 1.6 }}
              >
                <div className="flex items-center space-x-2">
                  <motion.div
                    className="w-1 h-1 bg-green-400 rounded-full"
                    animate={{ opacity: [1, 0.3, 1] }}
                    transition={{ duration: 1, repeat: Number.POSITIVE_INFINITY }}
                  />
                  <span className="text-green-400">SYSTEM_ONLINE</span>
                </div>
                <div className="text-gray-500">ENCRYPTION: AES-256</div>
              </motion.div>
            </div>
          </motion.div>
        </div>
      </div>
    </section>
  )
}

export default RobotContactForm
